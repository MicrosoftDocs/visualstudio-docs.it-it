---
title: Debug in modalità mista per Python | Microsoft Docs
description: Come eseguire il debug contemporaneamente di C++ e Python in Visual Studio inclusi il passaggio tra gli ambienti, la visualizzazione dei valori e la valutazione delle espressioni.
ms.custom: ''
ms.date: 01/16/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
- C++
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4f555e24c1328a4d784e3f8c5b2d0f1a7c590f8b
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="debugging-python-and-c-together"></a>Debug di codice Python e C++ in contemporanea

La maggior parte dei normali debugger Python supporta solo il debug di codice Python. Nella pratica, tuttavia, Python viene usato in combinazione con C o C++ in scenari che richiedono prestazioni elevate o la possibilità di richiamare direttamente le API della piattaforma. Per una procedura dettagliata, vedere [Creazione di un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md).

Visual Studio offre funzionalità di debug in modalità mista simultaneo integrato per codice Python e C/C++ nativo, a condizione di selezionare l'opzione **Strumenti di sviluppo nativi Python** per il carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio.

> [!Note]
> Il debug in modalità mista non è disponibile in Python Tools for Visual Studio 1.x in Visual Studio 2015 e versioni precedenti.

Le funzionalità di debug in modalità mista includono le seguenti, come illustrato in questo articolo:

- Stack di chiamate combinato
- Passaggio tra codice Python e codice nativo
- Punti di interruzione in entrambi i tipi di codice
- Visualizzazione delle rappresentazioni di Python di oggetti nei frame nativi e viceversa
- Debug all'interno del contesto del progetto Python o del progetto C++

![Debug in modalità mista](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | Per un'introduzione a compilazione, test e debug dei moduli C nativi con Visual Studio, vedere [Deep Dive: Creating Native Modules](https://youtu.be/D9RlT06a1EI) (Approfondimento: creazione di moduli nativi) (youtube.com, 9m 09s). Il video è applicabile sia a Visual Studio 2015 che a Visual Studio 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Abilitare il debug in modalità mista in un progetto Python

1. Fare clic con il pulsante destro del mouse sul progetto Python in Esplora soluzioni, scegliere **Proprietà**, selezionare la scheda **Debug** e quindi selezionare **Abilita debug codice nativo** . Questa opzione abilita la modalità mista per tutte le sessioni di debug.

    ![Abilitazione del debug di codice nativo](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Quando si abilita il debug del codice nativo, è possibile che la finestra di output di Python venga chiusa immediatamente al completamento del programma senza visualizzare il messaggio "Premere un tasto qualsiasi per continuare". Per specificare una pausa, aggiungere l'opzione `-i` al campo **Esegui > Argomenti dell'interprete** della scheda **Debug** quando si abilita il debug del codice nativo. Questo argomento fa passare l'interprete di Python in modalità interattiva al termine del codice e attende che vengano premuti CTRL+Z, INVIO per uscire.

1. Quando si collega il debugger in modalità mista a un processo esistente (**Debug > Connetti a processo**), usare il pulsante **Seleziona** per aprire la finestra di dialogo **Seleziona tipo di codice**. Impostare quindi l'opzione **Esegui il debug di questi tipi di codice** e selezionare sia **Nativo** che **Python** nell'elenco:

    ![Selezione dei tipi di codice nativo e Python](media/mixed-mode-debugging-code-type.png)

    Le impostazioni del tipo di codice sono persistenti, quindi se si vuole disabilitare il debug in modalità mista quando ci si collega a un altro processo in un secondo momento, deselezionare il tipo di codice Python.

    È possibile selezionare altri tipi di codice in aggiunta, o in sostituzione del tipo **Nativo**. Ad esempio, se un'applicazione gestita ospita CPython, che a sua volta usa moduli di estensione nativi e si vuole eseguire il debug di tutti e tre, è possibile selezionare **Python**, **Nativo** e **Gestito** insieme per un'esperienza di debug unificata, inclusi stack di chiamate combinati e la possibilità di passare tra tutti e tre i runtime.

1. Quando si avvia il debug in modalità mista per la prima volta, è possibile che venga visualizzata una finestra di dialogo **Simboli Python necessari**(vedere [Simboli per il debug in modalità mista](debugging-symbols-for-mixed-mode-c-cpp-python.md)). È necessario installare i simboli una sola volta per qualsiasi ambiente Python specificato. I simboli vengono inclusi automaticamente se si installa il supporto di Python tramite il programma di installazione di Visual Studio 2017.

1. Per rendere disponibile il codice sorgente per Python standard durante il debug, visitare [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/), scaricare l'archivio appropriato per la versione ed estrarlo in una cartella. È quindi possibile fare in modo che Visual Studio punti a file specifici nella cartella ogni volta che verrà richiesto.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Abilitare il debug in modalità mista in un progetto C/C++

Visual Studio 2017 (versione 15.5 e versioni successive) supporta il debug in modalità mista da un progetto C/C++, ad esempio quando si [incorpora codice Python in un'altra applicazione, come descritto in python.org](https://docs.python.org/3/extending/embedding.html). Per abilitare il debug in modalità mista, configurare il progetto C/C++ per avviare il "Debug Python/nativo":

1. Fare clic con il pulsante destro del mouse sul progetto C/C++ in Esplora soluzioni e scegliere **Proprietà**.
1. Selezionare la scheda **Debug**, selezionare "Debug Python/nativo" in **Debugger da avviare** e selezionare **OK**.

    ![Selezione del debugger Python/nativo in un progetto C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

Quando si usa questo metodo, tenere presente che non è possibile eseguire il debug dell'utilità di avvio di `py.exe` stessa, perché genera un processo figlio `python.exe` a cui non verrà collegato il debugger. Se si vuole avviare `python.exe` direttamente con argomenti, modificare l'opzione **Comando** nelle proprietà di Debug Python/nativo (illustrate nella figura precedente) per specificare il percorso completo di `python.exe`, quindi specificare gli argomenti in **Argomenti del comando**.

### <a name="attaching-the-mixed-mode-debugger"></a>Collegare il debugger in modalità mista

Per tutte le versioni precedenti di Visual Studio, il debug in modalità mista diretto viene abilitato solo quando si avvia un progetto Python in Visual Studio, perché i progetti C/C++ usano solo il debugger nativo. È comunque possibile collegare il debugger separatamente:

1. Avviare il progetto C++ senza eseguire il debug (**Debug > Avvia senza eseguire debug** o CTRL + F5).
1. Selezionare **Debug > Connetti a processo**. Nella finestra di dialogo visualizzata selezionare il processo appropriato, quindi usare il pulsante **Seleziona** per aprire la finestra di dialogo **Seleziona tipo di codice** in cui è possibile selezionare Python:

    ![Selezione di Python come tipo di debug quando si allega un debugger](media/mixed-mode-debugging-attach-type.png)

1. Selezionare **OK** per chiudere la finestra di dialogo e quindi **Allega** per avviare il debugger.
1. Potrebbe essere necessario introdurre una pausa o un ritardo nell'app C++ per assicurarsi che non chiami il codice Python di cui si vuole eseguire il debug prima di avere la possibilità di collegare il debugger.

## <a name="mixed-mode-specific-features"></a>Funzionalità specifiche della modalità mista

- [Stack di chiamate combinato](#combined-call-stack)
- [Passaggio tra codice Python e codice nativo](#stepping-between-python-and-native-code)
- [Visualizzazione di valori PyObject nel codice nativo](#pyobject-values-view-in-native-code)
- [Visualizzazione di valori nativi nel codice Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Stack di chiamate combinato

La finestra Stack di chiamate mostra sia gli stack frame nativi che di Python con interleave, con le transizioni contrassegnate tra i due:

![Stack di chiamate combinato](media/mixed-mode-debugging-call-stack.png)

Le transizioni vengono visualizzate come "[Codice esterno]", senza specificare la direzione della transizione, se è impostata l'opzione **Strumenti > Opzioni > Debug > Generale > Abilita Just My Code**.

È possibile fare doppio clic su qualsiasi frame di chiamata per attivarlo e per aprire il codice sorgente appropriato, se possibile. Se il codice sorgente non è disponibile, il frame viene comunque attivato ed è possibile controllare le variabili locali.

### <a name="stepping-between-python-and-native-code"></a>Passaggio tra codice Python e codice nativo

Quando si usano i comandi Esegui istruzione (F11) o Esci da istruzione/routine (MAIUSC+F11), il debugger in modalità mista gestisce correttamente le modifiche tra i tipi di codice. Ad esempio, quando Python chiama un metodo di un tipo implementato in C, l'esecuzione di istruzioni in una chiamata a tale metodo si interrompe all'inizio della funzione nativa che implementa il metodo. Analogamente, quando il codice nativo chiama una funzione API Python, ciò causa la chiamata del codice Python. Ad esempio, l'esecuzione di `PyObject_CallObject` per un valore di funzione originariamente definito in Python si interrompe all'inizio della funzione Python. Il passaggio da codice Python a codice nativo è supportato anche per le funzioni native richiamate da Python tramite [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Visualizzazione di valori PyObject nel codice nativo

Quando è attivo un frame nativo (C o C++), le relative variabili locali vengono visualizzate nella finestra Variabili locali del debugger. Nei moduli di estensione Python nativi, molte di queste variabili sono di tipo `PyObject` (ovvero un typedef per `_object`) o di alcuni altri tipi di Python fondamentali (vedere l'elenco riportato di seguito). Nel debug in modalità mista, per questi valori esiste un nodo figlio aggiuntivo denominato "visualizzazione Python". Quando viene espanso, questo nodo illustra la rappresentazione Python della variabile, identica a quella che si vedrebbe se in un frame Python fosse presente una variabile locale che fa riferimento allo stesso oggetto. Gli elementi figlio di questo nodo sono modificabili.

![Python View (Visualizzazione Python)](media/mixed-mode-debugging-python-view.png)

Per disabilitare questa funzionalità, fare clic con il pulsante destro del mouse in qualsiasi punto della finestra Variabili locali e disattivare l'opzione di menu **Python > Show Python View Nodes** (Mostra nodi visualizzazione Python):

![Abilitazione del nodo Python View (Visualizzazione Python)](media/mixed-mode-debugging-enable-python-view.png)

Tipi C che mostrano i nodi "[Python View]" (Visualizzazione Python), se abilitati:

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

Il nodo "[Python View]"(Visualizzazione Python) non viene visualizzato automaticamente per i tipi creati dall'utente. Quando si creano estensioni per Python 3. x, questo in genere non è un problema perché qualsiasi oggetto ha fondamentalmente un campo `ob_base` di uno dei tipi indicati in precedenza e quindi il nodo "[Vista Python]" viene visualizzato.

Per Python 2. x, tuttavia, ogni tipo di oggetto dichiara in genere l'intestazione come raccolta di campi inline e non esiste alcuna associazione tra i tipi personalizzati creati e `PyObject` a livello del sistema dei tipi nel codice C/C++. Per abilitare i nodi "[Vista Python]"per questi tipi personalizzati, modificare `PythonDkm.natvis` nella [directory di installazione di Python Tools](installing-python-support-in-visual-studio.md#install-locations) e aggiungere un altro elemento nel codice XML per lo struct C o la classe C++.

Un'opzione alternativa (e migliore) consiste nel seguire la proposta [PEP 3123](http://www.python.org/dev/peps/pep-3123/) e usare un campo `PyObject ob_base;` esplicito invece di `PyObject_HEAD`, sebbene ciò non sia sempre possibile per motivi di compatibilità con le versioni precedenti.

### <a name="native-values-view-in-python-code"></a>Visualizzazione di valori nativi nel codice Python

In modo simile a quanto descritto nella sezione precedente, è possibile abilitare un nodo "[C++ View]" (Visualizzazione C++) per i valori nativi nella finestra Variabili locali quando è attivo un frame Python. Questa funzionalità non è abilitata per impostazione predefinita, quindi per attivarla è necessario fare clic con il pulsante destro del mouse nella finestra Variabili locali e attivare l'opzione di menu **Python > Show C++ View Nodes** (Mostra nodi visualizzazione C++).

![Abilitazione del nodo C++ View (Visualizzazione C++)](media/mixed-mode-debugging-enable-cpp-view.png)

Il nodo "[C++ View]" (Visualizzazione C++) offre una rappresentazione della struttura C/C++ sottostante per un valore, identica a quella che verrebbe visualizzata in un frame nativo. Ad esempio, visualizza un'istanza di `_longobject` (per cui `PyLongObject` è un typedef) per un valore long integer Python e tenta di dedurre i tipi per le classi native create dall'utente. Gli elementi figlio di questo nodo sono modificabili.

![C++ View (Visualizzazione C++)](media/mixed-mode-debugging-cpp-view.png)

Se un campo figlio di un oggetto è di tipo `PyObject` o di uno degli altri tipi supportati, ha un nodo per la rappresentazione "[Vista Python]", se tali rappresentazioni sono abilitate, in modo che sia possibile esplorare gli oggetti grafici quando i collegamenti non sono esposti direttamente per Python.

Diversamente dai nodi "[Python View]" (Visualizzazione Python) che usano i metadati degli oggetti Python per determinare il tipo dell'oggetto, non esiste un meccanismo affidabile simile per i nodi "[C++ View]" (Visualizzazione C++). In termini generali, dato un valore Python, ovvero un riferimento a `PyObject`, non è possibile determinare in modo affidabile la struttura C/C++ sottostante. Il debugger in modalità mista tenta di dedurre il tipo esaminando i vari campi del tipo dell'oggetto (ad esempio `PyTypeObject` a cui fa riferimento il campo `ob_type` corrispondente) che hanno tipi di puntatore a funzione. Se uno di questi puntatori a funzione fa riferimento a una funzione che può essere risolta e tale funzione ha un parametro `self` con un tipo più specifico di `PyObject*`, si presuppone che tale tipo sia il tipo sottostante. Ad esempio, se `ob_type->tp_init` di un oggetto specificato fa riferimento alla funzione seguente:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

il debugger può dedurre correttamente che il tipo C dell'oggetto sia `FobObject`. Se non è possibile determinare un tipo più preciso da `tp_init`, il debugger passa ad altri campi. Se non è in grado di dedurre il tipo da uno qualsiasi di tali campi, il nodo "[C++ View]" (Visualizzazione C++) presenta l'oggetto come istanza di `PyObject`.

Per ottenere sempre una rappresentazione utile per i tipi personalizzati creati, è consigliabile registrare almeno una funzione speciale quando si registra il tipo e usare un parametro `self` fortemente tipizzato. La maggior parte dei tipi soddisfa questo requisito naturalmente. In caso contrario, `tp_init` è in genere la voce più comoda da usare per questo scopo. Un'implementazione fittizia di `tp_init` per un tipo che è presente unicamente per abilitare l'inferenza del tipo per il debugger può semplicemente restituire zero immediatamente, come nell'esempio di codice riportato sopra.

## <a name="differences-from-standard-python-debugging"></a>Differenze rispetto al debug Python standard

Il debugger in modalità mista è diverso dal [debugger Python standard](debugging-python-in-visual-studio.md) in quanto introduce alcune funzionalità aggiuntive, ma non include alcune funzionalità relative a Python:

- Funzionalità non supportate: punti di interruzione condizionali, finestra interattiva di debug e debug remoto multipiattaforma.
- Finestra di controllo immediato: è disponibile ma con un sottoinsieme limitato di funzionalità, tra cui tutte le limitazioni qui elencate.
- Versioni di Python supportate: solo CPython 2.7 e versioni successive alla 3.3.
- Visual Studio Shell: quando si usa Python con Visual Studio Shell, ad esempio se è stato installato con il programma di installazione integrato, Visual Studio non è in grado di aprire i progetti C++ e l'esperienza di modifica per i file di C++ è limitata a un semplice editor di testo. Il debug di C/C++ e il debug in modalità mista sono tuttavia supporti completamente nella shell con il codice sorgente, l'esecuzione istruzione per istruzione del codice nativo e la valutazione delle espressioni C++ nelle finestre del debugger.
- Visualizzazione ed espansione degli oggetti: durante la visualizzazione di oggetti Python nelle finestre del debugger Variabili locali ed Espressioni di controllo, il debugger in modalità mista mostra solo la struttura degli oggetti. Non valuta automaticamente le proprietà, né mostra gli attributi calcolati. Per le raccolte, mostra solo gli elementi per i tipi di raccolta predefiniti (`tuple`, `list`, `dict`, `set`). I tipi di raccolta personalizzati non vengono visualizzati come raccolte, a meno che non siano ereditati da un tipo di raccolta predefinito.
- Valutazione delle espressioni: vedere di seguito.

### <a name="expression-evaluation"></a>Valutazione delle espressioni

Il debugger Python standard consente la valutazione di espressioni arbitrarie di Python nelle finestre Espressioni di controllo e Controllo immediato quando il processo di debug viene sospeso in qualsiasi punto nel codice, a condizione che non sia bloccato in un'operazione di I/O o in altre chiamate di sistema simili. Durante il debug in modalità mista, possono essere valutate espressioni arbitrarie solo quando interrotte all'interno del codice Python, dopo un punto di interruzione o durante l'esecuzione di istruzioni nel codice. Le espressioni possono essere valutate solo per il thread in cui è presente il punto di interruzione o viene eseguita l'operazione di debug passo a passo.

In caso di arresto nel codice nativo, o nel codice Python quando non sono applicabili le condizioni sopra riportate (ad esempio, dopo un'operazione di uscita dall'istruzione o in un thread diverso), la valutazione delle espressioni si limita all'accesso alle variabili locali e globali nell'ambito del frame selezionato, all'accesso ai relativi campi e all'indicizzazione dei tipi di raccolta predefiniti con valori letterali. L'espressione seguente, ad esempio, può essere valutata in qualsiasi contesto, a condizione che tutti gli identificatori facciano riferimento a variabili e campi esistenti con tipi appropriati:

```python
foo.bar[0].baz['key']
```

Il debugger in modalità mista risolve anche queste espressioni in modo diverso. Tutte le operazioni di accesso ai membri cercano solo i campi che fanno parte direttamente dell'oggetto (come una voce in `__dict__` o `__slots__` oppure un campo di uno struct nativo esposto in Python tramite `tp_members`) e ignorano `__getattr__`, `__getattribute__` o logica di descrittore. In modo analogo, tutte le operazioni di indicizzazione ignorano `__getitem__` e accedono direttamente alle strutture dei dati interne delle raccolte.

Per mantenere la coerenza, questo schema di risoluzione dei nomi viene usato per tutte le espressioni che corrispondono ai vincoli per la valutazione delle espressioni limitate, indipendentemente dal fatto che le espressioni arbitrarie siano consentite o meno in corrispondenza del punto di interruzione corrente. Per forzare la semantica di Python appropriata quando è disponibile un analizzatore completo, racchiudere l'espressione tra parentesi:

```python
(foo.bar[0].baz['key'])
```