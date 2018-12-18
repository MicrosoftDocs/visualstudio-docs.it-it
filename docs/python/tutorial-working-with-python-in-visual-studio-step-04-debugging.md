---
title: Utilizzo di Python in Visual Studio, Passaggio 4, Debug | Microsoft Docs
description: Passaggio 4 di un'esercitazione di base per l'utilizzo di Python all'interno di Visual Studio, su come eseguire il codice Python nel debugger.
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ed662831d37d466a89b2899b2e6822509b22c9a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="step-4-running-code-in-the-debugger"></a>Passaggio 4: Esecuzione del codice nel debugger

**Passaggio precedente: [Uso della finestra interattiva REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Oltre a consentire di gestire i progetti, rendendo disponibili un'esperienza di modifica completa e la finestra interattiva, Visual Studio offre il debug completo per il codice Python. Nel debugger, è possibile eseguire il codice in dettaglio, incluse le interazioni di un ciclo. È anche possibile sospendere il programma ogni volta che vengono soddisfatte determinate condizioni. Quando il programma viene sospeso nel debugger, è possibile esaminare in qualsiasi momento lo stato dell'intero programma e modificare il valore di variabili. Tali azioni sono essenziali per individuare i bug del programma e offrire supporto per seguire attentamente il flusso esatto del programma.

1. Sostituire il codice nel file `PythonApplication1.py` con il codice seguente. Questa variante del codice espande `make_dot_string` in modo da poter esaminare i passaggi discreti nel debugger. Inserisce anche il ciclo `for` in una funzione `main` e lo esegue in modo esplicito chiamando la funzione:

    ```python
    import sys
    from math import sin, cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        str = ' ' * numspaces + 'o'                  # place 'o' after the spaces
        return str

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Controllare che il codice funzioni correttamente. A tale scopo, premere F5 o selezionare il comando di menu **Debug > Avvia debug**. Il comando esegue il codice nel debugger. Dato che non sono impostate pause per l'esecuzione del programma, stampa semplicemente un motivo ondulato per alcune iterazioni. Premere un tasto qualsiasi per chiudere la finestra di output.

    > [!Tip]
    > Per chiudere la finestra di output automaticamente dopo il completamento del programma, sostituire la chiamata `main()` con il codice seguente:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Impostare un punto di interruzione sull'istruzione `for` facendo clic nel margine grigio a sinistra della riga oppure posizionare il cursore nella riga e usare il comando **Debug > Impost/Rimuovi punto di interruzione** (F9). Sul margine grigio viene visualizzato un punto rosso per indicare il punto di interruzione, come indicato dalla freccia blu di seguito:

    ![Impostazione di un punto di interruzione](media/vs-getting-started-python-18-debugging1.png)

1. Avviare di nuovo il debugger (F5). Si può vedere che l'esecuzione del codice si interrompe in corrispondenza della riga con il punto di interruzione. È così possibile analizzare lo stack di chiamate ed esaminare le variabili locali. Le variabili incluse nell'ambito, quando definite, vengono visualizzati nella finestra **Auto** ; è anche possibile passare alla visualizzazione **Variabili locali** nella parte inferiore della finestra per visualizzare tutte le variabili che Visual Studio individua nell'ambito attuale (funzioni incluse), comprese quelle non ancora definite:

    ![Esperienza dell'interfaccia utente per i punti di interruzione per Python](media/vs-getting-started-python-19-debugging2b.png)

1. Osservare la barra degli strumenti di debug (visualizzata di seguito) nella parte superiore della finestra di Visual Studio. Questa barra degli strumenti consente di accedere rapidamente ai comandi di debug più comuni (disponibili nel menu **Debug**):

    ![Pulsanti essenziali della barra degli strumenti di debug](media/vs-getting-started-python-20-debugging3.png)

    I pulsanti da sinistra a destra nel modo seguente:
    - **Continua** (F5) esegue il programma fino al punto di interruzione successivo o fino al completamento del programma.
    - **Interrompi tutto** (CTRL+ALT+BREAK) consente di sospendere un programma con esecuzione prolungata.
    - **Termina debug** (MAIUSC+F5) arresta il programma in qualsiasi punto e chiude il debugger.
    - **Riavvia** (CTRL+MAIUSC+F5) arresta il programma in qualsiasi punto e lo riavvia dall'inizio nel debugger.
    - **Mostra istruzione successiva** (ALT+NUM *) passa alla riga successiva del codice da eseguire. Questo è particolarmente utile per spostarsi all'interno del codice durante una sessione di debug e tornare rapidamente al punto in cui il debugger si è interrotto.
    - **Esegui istruzione** (F11) esegue la riga successiva del codice, inserendosi nelle funzioni chiamate.
    - **Esegui istruzione/routine** (F10) esegue la riga successiva del codice, senza inserirsi nelle funzioni chiamate.
    - **Esci da istruzione/routine** (Shift+F11) esegue la parte restante della funzione corrente e le pause nel codice chiamante.

1. Eseguire l'istruzione/routine `for` usando **Esegui istruzione/routine**. L'*esecuzione di istruzioni* prevede l'esecuzione della linea di codice corrente da parte del debugger, incluse le chiamate di funzione, e poi di nuovo una pausa immediata. Si noti come la variabile `i` è ora definita nelle finestre **Variabili locali** e **Auto**.

1. Eseguire l'istruzione/routine alla riga successiva del codice che chiama `make_dot_string` e si sospende. L'esecuzione dell'istruzione/routine significa che il debugger esegue l'intero `make_dot_string` e, una volta restituito, si sospende. Il debugger non si arresta all'interno della funzione a meno che non sia presente un punto di interruzione separato.

1. Ripetere altre volte l'esecuzione dell'istruzione/routine e osservare in che modo si modificano i valori **Variabili locali** o **Auto**.

1. Nella finestra **Variabili locali** o **Auto** fare doppio clic sulla colonna **Valore** per le variabili `i` o `s` per modificare il valore. Premere INVIO oppure fare clic all'esterno di tale valore per applicare eventuali modifiche.

1. Continuare l'esecuzione nel codice usando **Esegui istruzione**. Esegui istruzione indica che il debugger viene inserito all'interno di una qualsiasi chiamata di funzione per la quale ha informazioni di debug, ad esempio `make_dot_string`. Una volta dentro a `make_dot_string` è possibile esaminare le variabili locali ed eseguire i passaggi nel codice.

1. Continuare l'esecuzione con Esegui istruzione. Si noti che quando si raggiunge la fine di `make_dot_string`, il passaggio successivo restituisce al ciclo `for` il nuovo valore restituito nella variabile `s`. Mentre si esegue di nuovo l'istruzione `print`, si noti che Esegui istruzione in `print` non entra in tale funzione. Questo si verifica perché `print` non è scritto in Python ma è un codice nativo che si trova all'interno del runtime di Python.

1. Continuare a usare Esegui istruzione fino a quando non si è nuovamente in `make_dot_string`. Quindi usare **Esci da istruzione/routine**. Si noti che si è fatto ritorno al ciclo `for`. Con Esci da istruzione/routine, il debugger esegue il resto della funzione e quindi si sospende automaticamente nel codice chiamante. Ciò è molto utile per quelle porzioni delle funzioni di lunga durata su cui si vuole eseguire il debug ma senza eseguire il resto della funzione un'istruzione alla volta né impostare un punto di interruzione esplicito nel codice chiamante.

1. Per continuare l'esecuzione del programma, fino a quando non viene raggiunto il punto di interruzione successivo, usare **Continua** (F5). Dato che il ciclo `for` contiene un punto di interruzione, l'esecuzione viene interrotta nell'iterazione successiva.

1. Scorrere centinaia di iterazioni di un ciclo può risultare noioso, pertanto in Visual Studio è possibile aggiungere una *condizione* a un punto di interruzione. Il debugger sospende quindi il programma nel punto di interruzione solo quando la condizione viene soddisfatta. Ad esempio, è possibile usare una condizione con il punto di interruzione sull'istruzione `for` in modo che non venga sospeso solo quando il valore di `i` supera 1600. Per impostare questa condizione, fare clic con il pulsante destro del mouse sul punto rosso del punto di interruzione e scegliere **Condizioni...** (ALT+F9,C). Nella finestra **Impostazioni punto di interruzione** visualizzata immettere `i > 1600` come espressione e selezionare **Chiudi**. Premere F5 per continuare e osservare che il programma esegue diverse iterazioni prima del punto di interruzione successivo.

    ![Impostazione di una condizione per il punto di interruzione](media/vs-getting-started-python-21-debugging4.png)

1. Per eseguire il programma fino al completamento, disabilitare il punto di interruzione facendo clic col pulsante destro del mouse e selezionando **Disattiva punto di interruzione** (CTRL+F9). Quindi selezionare **Continua** (o premere F5) per eseguire il programma. Quando termina, Visual Studio arresta la sessione di debug e restituisce la modalità di modifica. Si noti che è anche possibile eliminare il punto di interruzione facendo clic sul relativo punto. Questa procedura, tuttavia, elimina anche qualsiasi condizione impostata in precedenza.

> [!Tip]
> In alcune situazioni, come ad esempio quando si verifica un errore durante l'avvio dell'interprete Python stesso, la finestra di output potrebbe essere visualizzata solo per pochissimo tempo e poi chiudersi automaticamente, impedendo la visualizzazione dei messaggi di errore. Se questo dovesse verificarsi, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, selezionare **Proprietà**, selezionare la scheda **Debug**, quindi aggiungere `-i` al campo **Argomenti dell'interprete**. Questo argomento fa sì che l'interprete passi in modalità interattiva dopo il completamento di un programma, mantenendo la finestra aperta fino a quando non viene premuto CTRL+Z, INVIO per chiuderla.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Installazione dei pacchetti nell'ambiente Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

### <a name="going-deeper"></a>Approfondimenti

- [Debug](debugging-python-in-visual-studio.md)
- Vedere [Debug in Visual Studio](../debugger/debugger-feature-tour.md) per la documentazione completa sulle funzionalità di debug di Visual Studio.
