---
title: Uso di C++ e Python in Visual Studio | Microsoft Docs
description: Processo e passaggi per scrivere un modulo o un'estensione di C++ per Python in Visual Studio
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
- C++
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 31d36ede3293a72db06e9919545dafb779cee252
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="creating-a-c-extension-for-python"></a>Creazione di un'estensione C++ per Python

I moduli scritti in C++ (o in C) vengono comunemente usati per estendere le funzionalità di un interprete Python e anche per abilitare l'accesso alle funzionalità di basso livello del sistema operativo. Sono disponibili tre tipi primari di moduli:

- Moduli acceleratori: dato che Python è un linguaggio interpretato, determinati frammenti di codice possono essere scritti in C++ per ottenere migliori prestazioni. 
- Moduli wrapper: i wrapper espongono al codice Python le interfacce C/C++ esistenti o un'API più facilmente utilizzabile da Python.
- Moduli di accesso al sistema di basso livello: creati per accedere alle funzionalità di basso livello del runtime di CPython, al sistema operativo o all'hardware sottostante.

Questo articolo illustra la creazione di un modulo di estensione C++ per CPython per calcolare una tangente iperbolica. Illustra anche come chiamare il modulo da codice Python. La routine viene implementata prima in Python per illustrare il miglioramento relativo delle prestazioni dell'implementazione della routine stessa in C++.

L'approccio adottato in questo argomento è quello per le estensioni CPython standard come illustrato nella [documentazione di Python](https://docs.python.org/3/c-api/). Un confronto tra questo e altri approcci viene illustrato in [Approcci alternativi](#alternative-approaches) alla fine di questo articolo.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 con i carichi di lavoro **Sviluppo di applicazioni desktop con C++** e **Sviluppo Python** installati con le opzioni predefinite.
- Nel carico di lavoro **Sviluppo Python** selezionare anche la casella **Strumenti di sviluppo nativo Python** a destra. Questa opzione imposta la maggior parte della configurazione descritta in questo articolo. Questa opzione include automaticamente anche il carico di lavoro C++.

![Selezione dell'opzione Strumenti di sviluppo nativo Python](media/cpp-install-native.png)

- L'installazione del carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati** include anche Python e l'opzione **Strumenti di sviluppo nativi Python** per impostazione predefinita.

Per altre informazioni, vedere [Installazione del supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md), che illustra l'uso di altre versioni di Visual Studio. Se si installa Python separatamente, assicurarsi di selezionare **Download debugging symbols** (Scarica i simboli di debug) e **Download debug binaries** (Scarica file binari di debug) nella sezione **Opzioni avanzate** del programma di installazione. Questa opzione consente di avere a disposizione le librerie di debug necessarie se si sceglie di eseguire una build di debug.

## <a name="create-the-python-application"></a>Creare un'applicazione Python

1. Creare un nuovo progetto di Python in Visual Studio selezionando **File > Nuovo > Progetto**. Cercare "Python", selezionare il modello **Applicazione Python**, assegnare a questo un nome e un percorso appropriati e selezionare **OK**.

1. Nel file `.py` del progetto, incollare il codice seguente che effettua il benchmark del calcolo di una tangente iperbolica, implementato senza usare la libreria matematica per un confronto più semplice. È anche possibile immettere il codice manualmente per provare alcune delle [funzionalità di modifica Python](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Eseguire il programma usando **Debug > Avvia senza eseguire debug** (Ctrl + F5) per visualizzare i risultati. È possibile modificare la variabile `COUNT` per modificare il tempo impiegato per l'esecuzione dei benchmark. Ai fini di questa procedura dettagliata, impostare il conteggio in modo che ogni benchmark richieda circa due secondi.

## <a name="create-the-core-c-project"></a>Creare un progetto di base C++

1. Fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e selezionare **Aggiungi > Nuovo progetto**. Una soluzione di Visual Studio può includere progetti Python e C++ insieme.

1. Cercare "C++", selezionare **Progetto vuoto**, specificare un nome (in questo articolo viene usato "superfastcode") e fare clic su **OK**. Nota: se sono stati installati gli **strumenti di sviluppo nativo Python** con Visual Studio 2017, è possibile iniziare con il modello **Modulo di estensione Python**, che include quasi tutti gli elementi descritti in questo argomento. Questa procedura dettagliata, tuttavia, inizia da un progetto vuoto e illustra la creazione del modulo di estensione in modo dettagliato.

1. Creare un file C++ nel nuovo progetto facendo clic con il pulsante destro del mouse sul nodo **File di origine**, selezionare **Aggiungi > Nuovo elemento**, selezionare **File C++**, assegnargli un nome (ad esempio `module.cpp`) e fare clic su **OK**. Questo passaggio è necessario per attivare le pagine delle proprietà C++ nei passaggi seguenti.

1. Fare clic con il pulsante destro del mouse sul progetto C++ in Soluzione e scegliere **Proprietà**.

1. Nella parte superiore della finestra di dialogo **Pagine delle proprietà** visualizzata impostare **Configurazione** su **Tutte le configurazioni** e **Piattaforma** su **Win32**.

1. Impostare le proprietà specifiche, come descritto nella tabella seguente e quindi selezionare **OK**.

    | Scheda | Proprietà | Valore |
    | --- | --- | --- |
    | Generale | Generale > Nome di destinazione | Specificare il nome del modulo quando si vuole fare riferimento a esso da Python in istruzioni `from...import`. Questo stesso nome viene usato in C++ quando si definisce il modulo per Python. Se si vuole usare il nome del progetto come nome del modulo, lasciare il valore predefinito di `$(ProjectName)`. |
    | | Generale > Estensione di destinazione | .pyd |
    | | Impostazioni predefinite del progetto > Tipo di configurazione | Libreria dinamica (.dll) |
    | C/C++ > Generale | Directory di inclusione aggiuntive | Aggiungere la cartella `include` di Python nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\include`.  |
    | C/C++ > Preprocessore | Definizioni del preprocessore | Aggiungere `Py_LIMITED_API;` all'inizio della stringa (incluso il punto e virgola). Questa definizione limita alcune delle funzioni che è possibile chiamare da Python e rende il codice più portatile tra versioni diverse di Python. |
    | C/C++ > Generazione codice | Libreria di runtime | DLL multithread (/MD) (vedere l'avviso di seguito) |
    | Linker > Generale | Directory librerie aggiuntive | Aggiungere la cartella `libs` di Python che include i file `.lib` nella maniera più appropriata per l'installazione, ad esempio `c:\Python36\libs`. Assicurarsi di indicare la cartella `libs` che contiene i file `.lib`, e *non* la cartella `Lib` che contiene i file `.py`. |

    > [!Tip]
    > Se la scheda C/C++ non è visualizzata nelle proprietà del progetto, il progetto non include alcun file identificato come file di origine C/C++. Questa condizione può verificarsi se si crea un file di origine senza un'estensione `.c` o `.cpp`. Ad esempio, se viene digitato per errore `module.coo` invece di `module.cpp` nella precedente finestra di dialogo del nuovo elemento, Visual Studio crea il file ma non imposta il tipo di file su "Codice C/C+," che attiva la scheda delle proprietà C/C++. Tale errore di identificazione permane anche se si rinomina il file con l'estensione `.cpp`. Per impostare correttamente il tipo di file, fare clic con il pulsante destro del mouse sul file in Esplora soluzioni, selezionare **Proprietà** e quindi impostare **Tipo di file** su **Codice C/C++**.

    > [!Warning]
    > Impostare sempre l'opzione **C/C++ > Generazione codice > Libreria di runtime** su "DLL multithread (/MD)", anche per una configurazione di debug, poiché questa è l'impostazione usata per compilare i file binari Python non di debug. Se si imposta l'opzione "DLL multithread (/MD)" e si compila una configurazione di debug, viene generato l'errore *C1189: Py_LIMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS, and Py_REF_DEBUG* (C1189: Py_LIMITED_API non è compatibile con Py_DEBUG, Py_TRACE_REFS e Py_REF_DEBUG). In aggiunta, se si rimuove `Py_LIMITED_API` per evitare l'errore di compilazione, l'esecuzione di Python si arresta in modo anomalo quando prova a importare il modulo. L'arresto anomalo del sistema si verifica all'interno della chiamata della DLL a `PyModule_Create`, come descritto più avanti, con il messaggio di output *Fatal Python error: PyThreadState_Get: no current thread* (Errore irreversibile di Python: PyThreadState_Get: nessun thread corrente).
    >
    > L'opzione /MDd viene usata per compilare file binari di debug di Python (ad esempio python_d.exe), ma la selezione di questa opzione per una DLL di estensione causa sempre un errore di compilazione con `Py_LIMITED_API`.

1. Fare clic con il pulsante destro del mouse sul progetto C++ e selezionare **Compila** per testare le configurazioni sia di debug che di versione. I file `.pyd` si trovano nella cartella *solution* all'interno delle sottocartelle **Debug** e **Release**, non nella cartella del progetto C++.

1. Aggiungere il codice seguente al file `.cpp` del progetto C++ principale:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Compilare di nuovo il progetto C++ per confermare che il codice sia corretto.

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertire il progetto C++ in un'estensione per Python

Per rendere disponibile la DLL C++ in un'estensione per Python, modificare prima i metodi esportati in modo che interagiscano con i tipi di Python. Aggiungere quindi una funzione che esporti il modulo, insieme alle definizioni dei metodi del modulo. Per informazioni generali su quanto illustrato di seguito, vedere [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) (Manuale di riferimento all'API Python/C) e in particolare [Module Objects](https://docs.python.org/3/c-api/module.html) (Oggetti del modulo) in python.org. Ricordarsi di selezionare la versione di Python dal controllo a discesa in alto a destra.

> [!Note]
> Queste istruzioni si applicano a Python 3.x. Se si lavora con Python 2.7, fare riferimento a [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html) (Estensione di Python 2.7 con C o C++) e [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html) (Conversione dei moduli di estensione per Python 3) (python.org).

1. Nel file C++, includere `Python.h` nella parte superiore:

    ```cpp
    #include <Python.h>
    ```

    > [!Tip]
    > Se viene visualizzato l'errore *E1696: cannot open source file "Python.h"* (E1696: impossibile aprire il file di origine "Python.h") e/o l'errore *C1083: Cannot open include file: "Python.h": No such file or directory* (C1083: impossibile aprire il file di inclusione "Python.h": file o directory non esistente), verificare di aver impostato **C/C++ > Generale > Directory di inclusione aggiuntive** nelle proprietà del progetto sulla cartella `include` dell'installazione Python in uso come descritto al passaggio 6 in [Creare un progetto di base C++](#create-the-core-c-project).

1. Modificare il metodo `tanh_impl` in modo che accetti e restituisca tipi di Python (ovvero un `PyOjbect*`):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Aggiungere una struttura che definisca come la funzione `tanh_impl` di C++ viene presentata a Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Aggiungere una struttura che definisca il modulo come si vuole farvi riferimento nel codice Python, in particolare quando si usa l'istruzione `from...import`. Fare in modo che questo corrisponda al valore nelle proprietà del progetto in **Proprietà di configurazione > Generale > Nome di destinazione**. Nell'esempio seguente, il nome di modulo "superfastcode" significa che è possibile usare `from superfastcode import fast_tanh` in Python, perché `fast_tanh` è definito all'interno di `superfastcode_methods`. (I nomi di file interni del progetto C++, come module.cpp, sono irrilevanti.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Aggiungere un metodo che verrà chiamato da Python quando carica il modulo, che deve essere denominato `PyInit_<module-name>` dove *&lt;module_name&gt;* corrisponde esattamente alla proprietà **Generale > Nome di destinazione** del progetto C++ (ovvero corrisponde al nome del file `.pyd` compilato dal progetto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Impostare la configurazione di destinazione su "Rilascio" e compilare di nuovo il progetto C++ per verificare il codice. Se si verificano errori, controllare i casi seguenti:
    - Non è possibile individuare Python.h: verificare che il percorso in **C/C++ > Generale > Directory di inclusione aggiuntive** nelle proprietà del progetto punti alla cartella `include` dell'installazione di Python in uso.
    - Non è possibile individuare le librerie Python: verificare che il percorso in **Linker > Generale > Directory librerie aggiuntive** nelle proprietà del progetto punti alla cartella `libs` dell'installazione di Python in uso.
    - Errori del linker correlati all'architettura di destinazione: modificare l'architettura di progetto della destinazione C++ in modo che corrisponda a quella dell'installazione di Python in uso.

## <a name="test-the-code-and-compare-the-results"></a>Testare il codice e confrontare i risultati

Ora che la libreria è strutturata come estensione per Python, è possibile fare riferimento a tale libreria dal progetto Python, importare il modulo e usare i metodi.

### <a name="make-the-dll-available-to-python"></a>Rendere disponibile la DLL per Python

Ci sono due modi per rendere disponibile la DLL per Python.

Il primo metodo funziona se il progetto Python e il progetto C++ sono nella stessa soluzione. Passare a Esplora soluzioni, fare clic con il pulsante destro del mouse sul nodo **Riferimenti** nel progetto Python e quindi scegliere **Aggiungi riferimento**. Nella finestra di dialogo visualizzata selezionare la scheda **Progetti**, selezionare il progetto **superfastcode** (o qualsiasi nome usato) e quindi fare clic su **OK**.

Il metodo alternativo, descritto nei passaggi seguenti, consente di installare il modulo nell'ambiente di Python globale, rendendolo disponibile anche per altri progetti Python. Questo in genere richiede di aggiornare il database di completamento IntelliSense per tale ambiente. L'aggiornamento è necessario anche quando si rimuove il modulo dall'ambiente.

1. Se si usa Visual Studio 2017, eseguire il programma di installazione di Visual Studio, selezionare **Modifica**, selezionare **Singoli componenti > Compilatori, strumenti di compilazione e runtime > Set di strumenti di Visual C++ 2015.3 v140**. Questo passaggio è necessario perché Python (per Windows) è esso stesso compilato con Visual Studio 2015 (versione 14.0) e richiede la disponibilità di questi strumenti quando compila un'estensione tramite il metodo descritto in questo argomento. Si noti che può essere necessario installare una versione a 32 bit di Python e usare come destinazione della DLL Win32 e non x64.

1. Creare un file denominato `setup.py` nel progetto C++ facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Aggiungi > Nuovo elemento**. Selezionare quindi "File di C++ (.cpp)", assegnare il nome `setup.py` al file e selezionare **OK**. L'assegnazione di un nome al file con estensione `.py` consente di fare in modo che Visual Studio lo riconosca come Python nonostante l'uso del modello di file C++. Quando il file viene visualizzato nell'editor, incollarvi il codice seguente:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Per documentazione su questo script, vedere [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (Compilazione di estensioni C e C++) in python.org.

1. Il codice `setup.py` indica a Python di compilare l'estensione usando il set di strumenti di Visual Studio 2015 C++ dalla riga di comando. Aprire un prompt dei comandi con privilegi elevati, passare alla cartella contenente il progetto C++ (ovvero la cartella contenente `setup.py`) e immettere il comando seguente:

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Chiamare la DLL da Python

Dopo aver eseguito uno dei metodi precedenti, è ora possibile chiamare la funzione `fast_tanh` da codice Python e confrontarne le prestazioni con l'implementazione Python:

1. Aggiungere le righe seguenti nel file `.py` per chiamare il metodo `fast_tanh` esportato dalla DLL e visualizzarne l'output.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Eseguire il programma Python (**Debug > Avvia senza eseguire debug** o Ctrl + F5) e osservare che la routine C++ viene eseguita da 5 a 20 volte più velocemente rispetto all'implementazione Python. Provare di nuovo a incrementare la variabile `COUNT` in modo che le differenze siano più evidenti. Si noti anche che una build di debug del modulo C++ viene eseguita più lentamente rispetto a una build di rilascio perché la build di debug è meno ottimizzata e contiene vari controlli degli errori. È possibile alternare liberamente queste configurazioni ai fini del confronto.

## <a name="debug-the-c-code"></a>Eseguire il debug del codice C++

Visual Studio supporta il debug di codice Python e C++ insieme.

1. Fare clic con il pulsante destro del mouse sul progetto Python in Esplora soluzioni, selezionare **Proprietà**, selezionare la scheda **Debug** e quindi selezionare l'opzione **Debug > Abilita debug codice nativo** .

    > [!Tip]
    > Quando si abilita il debug del codice nativo, è possibile che la finestra di output di Python venga chiusa quando il programma avrà terminato l'operazione, senza che venga visualizzato il consueto messaggio "Premere un tasto qualsiasi per continuare". Per specificare una pausa, aggiungere l'opzione `-i` al campo **Esegui > Argomenti dell'interprete** della scheda **Debug** quando si abilita il debug del codice nativo. Questo argomento fa passare l'interprete di Python in modalità interattiva al termine del codice e attende che vengano premuti CTRL+Z, INVIO per uscire. In alternativa, se si vuole modificare il codice Python, è possibile aggiungere le istruzioni `import os` e `os.system("pause")` alla fine del programma. Questo codice duplica la richiesta di pausa originale.

1. Selezionare **File > Salva** per salvare le modifiche delle proprietà.

1. Impostare la configurazione della build su "Debug" sulla barra degli strumenti di Visual Studio.

    ![Impostazione della configurazione di build su Debug](media/cpp-set-debug.png)

1. Dato che l'esecuzione del codice richiede in genere più tempo nel debugger, può essere utile modificare la variabile `COUNT` nel file `.py` impostando un valore inferiore di circa cinque volte (ad esempio, modificarlo da `500000` a `100000`).

1. Nel codice C++ impostare un punto di interruzione nella prima riga del metodo `tanh_impl` e quindi avviare il debugger (F5 or **Debug > Avvia debug**). Il debugger interrompe l'esecuzione quando viene chiamato tale codice. Se non viene raggiunto il punto di interruzione, controllare che la configurazione sia impostata su Debug e di aver salvato il progetto, operazione che non viene eseguita automaticamente all'avvio del debugger.

    ![Interruzione in un punto del codice C++](media/cpp-debugging.png)

1. A questo punto è possibile eseguire il codice C++ istruzione per istruzione, esaminare le variabili e così via. Queste funzionalità sono descritte in dettaglio in [Debug di codice Python e C++ in contemporanea](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Approcci alternativi

Esistono svariati modi per creare estensioni di Python, come descritto nella tabella seguente. La prima voce per CPython corrisponde a ciò che è già stato illustrato in questo articolo.

| Approccio | Anno | Utenti rappresentanti | Vantaggi | Svantaggi |
| --- | --- | --- | --- | --- |
| Moduli di estensione C/C++ per CPython | 1991 | Libreria standard | [Documentazione ampia ed esercitazioni](https://docs.python.org/3/c-api/). Controllo totale. | Compilazione, portabilità, gestione dei riferimenti. Conoscenza elevata di C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Genera associazioni per molte lingue contemporaneamente. | Sovraccarico eccessivo se Python è l'unica destinazione. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nessuna compilazione, ampia disponibilità. | Accesso e modifica di strutture C complesse e soggette a errori. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Simile a Python. Altamente maturo. Prestazioni elevate. | Compilazione, nuova sintassi, nuova toolchain. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilità di integrazione, compatibilità PyPy. | Nuovo, meno maturo. |
