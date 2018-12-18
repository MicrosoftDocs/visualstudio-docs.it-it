---
title: Eseguire il debug con il debugger di Visual Studio C++ | Documenti Microsoft
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f591c4272dc50643dcb3c82f60d96fd218723405
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>Eseguire il debug con C++ utilizzando il debugger di Visual Studio

Il debugger di Visual Studio fornisce molte funzionalità avanzate che consentono di eseguire il debug delle applicazioni. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

2. In **Visual C++** scegliere **Desktop di Windows** e nel riquadro al centro scegliere **Applicazione console di Windows**.

    Se non viene visualizzato il **applicazione Console di Windows** modello di progetto, fare clic sul **aprire Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** la finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **sviluppo di applicazioni Desktop con C++** carico di lavoro, quindi scegliere **modifica**.

3. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

4. In MyDbgApp.cpp sostituire il codice seguente

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con questo codice (non rimuovere `#include "stdafx.h"`):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

Oggetto *punto di interruzione* è un indicatore che segnala che in Visual Studio dovrebbe sospendere l'esecuzione di codice in modo da poter esaminare i valori delle variabili, il comportamento di memoria o o meno un ramo del codice di esecuzione di. È la funzionalità di base nel debug.

1. Per impostare il punto di interruzione, fare clic nella barra di navigazione a sinistra del `doWork` chiamata di funzione (o selezionare la riga di codice e premere **F9**).

    ![Impostare un punto di interruzione](../debugger/media/dbg-qs-set-breakpoint.png "impostare un punto di interruzione")

2. A questo punto premere **F5** (oppure scegliere **Debug > Avvia debug**).

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint.png "raggiunge un punto di interruzione")

    Le pause di debugger in cui è stato impostato il punto di interruzione. L'istruzione in cui viene sospesa l'esecuzione del debugger e app è indicato dalla freccia gialla. La riga con il `doWork` chiamata di funzione non è stata ancora eseguita.

    > [!TIP]
    > Se si dispone di un punto di interruzione in un ciclo o una ricorsione, o se si dispone di molti punti di interruzione che spesso un'istruzione alla volta, utilizzare un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per assicurarsi che il codice venga sospeso solo quando vengono soddisfatte specifiche condizioni. Un punto di interruzione condizionale consente di risparmiare tempo e possa inoltre semplificare il debug dei problemi che sono difficili da riprodurre.

    Quando si tenta di eseguire il debug di errori correlati alla memoria in C++, è possibile utilizzare anche i punti di interruzione per esaminare i valori di indirizzo (cercare NULL) e i conteggi di riferimento. 

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger di continuare. Viene illustrato un comando di spostamento di codice utile che è stato introdotto in Visual Studio 2017.

Mentre nel punto di interruzione in sospeso, passare il mouse sull'istruzione `c1.push_back(20)` fino a quando il verde **esecuzione fare clic su** pulsante ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata e quindi premere i **Esecuzione fare clic su** pulsante.

![Esecuzione di fare clic su](../debugger/media/dbg-qs-run-to-click.png "esecuzione fare clic su")

L'applicazione continua l'esecuzione, la chiamata `doWork`e posiziona nella riga di codice in cui si fa clic sul pulsante.

Comandi di tasti comuni utilizzati per eseguire il codice includono **F10** e **F11**. Per altre istruzioni dettagliate, vedere il [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Controllare le variabili in un suggerimento dati

1. Nella riga corrente di codice (contrassegnati con il puntatore di esecuzione giallo), passare il mouse su di `c1` oggetto con il mouse per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip.png "visualizzare un suggerimento dati")

    Il suggerimento dati mostra il valore corrente di `c1` variabile e consente di controllare le relative proprietà. Durante il debug, se viene visualizzato un valore che non si prevede che, probabilmente è un bug nelle righe precedenti o chiamate di codice. 

2. Espandere il suggerimento dati per esaminare i valori correnti delle proprietà di `c1` oggetto.

3. Se si desidera bloccare il suggerimento dati, in modo che è possibile continuare a visualizzare il valore di `c1` durante l'esecuzione di codice, fare clic sull'icona di piccole dimensioni pin. (È possibile spostare il suggerimento dati bloccato in una posizione comoda).

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se si rileva una modifica che si desidera testare nel codice durante l'esecuzione di una sessione di debug, è possibile farlo, troppo.

1. Scegliere la seconda istanza di `c2.front()` e modificare `c2.front()` a `c2.back()`.

2. Premere **F10** (o **Debug > Esegui istruzione/routine**) poche volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue.gif "modifica e continuazione")

    **F10** sposta in avanti l'istruzione debugger uno alla volta, ma i passaggi su funzioni anziché eseguire un'istruzione avervi (il codice che viene comunque eseguita).

Per ulteriori informazioni sull'utilizzo di modifica e continuazione e alle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger vengono forniti collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
