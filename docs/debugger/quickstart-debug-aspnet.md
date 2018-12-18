---
title: Eseguire il debug ASP.NET - Visual Studio | Documenti Microsoft
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c9cc8022a6080b63792cdadcc87af07e08ef749e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-aspnet-with-the-visual-studio-debugger"></a>Eseguire il debug di ASP.NET con il debugger di Visual Studio

Il debugger di Visual Studio fornisce molte funzionalità avanzate che consentono di eseguire il debug delle applicazioni. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. In **Visual c#**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web di ASP.NET Core**.

1. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

1. Nella finestra di dialogo visualizzata, scegliere **applicazione Web** nel riquadro centrale e quindi fare clic su **OK**.

     Se non viene visualizzato il **applicazione Web** modello di progetto, fare clic sul **aprire Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** la finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **ASP.NET** e **.NET Core** carico di lavoro, quindi scegliere **modifica**.

    ![Scegliere un'applicazione Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio crea il progetto.

1. In Esplora soluzioni, aprire About.cshtml.cs (in Pages/About.cshtml) e sostituire il codice seguente

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    con questo codice:

    ```c#
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

Oggetto *punto di interruzione* è un indicatore che segnala che in Visual Studio dovrebbe sospendere l'esecuzione di codice in modo da poter esaminare i valori delle variabili, il comportamento di memoria o o meno un ramo del codice di esecuzione di. È la funzionalità di base nel debug.

1. Per impostare il punto di interruzione, fare clic nella barra di navigazione a sinistra del `doWork` funzione (o selezionare la riga di codice e premere **F9**).

    ![Imposta punto di interruzione](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Il punto di interruzione è impostato a sinistra della parentesi graffa di apertura (`{`).

1. A questo punto premere **F5** (oppure scegliere **Debug > Avvia debug**).

1. Quando viene caricata la pagina web, fare clic su di **su** collegamento nella parte superiore della pagina web.

    Le pause di debugger in cui è stato impostato il punto di interruzione. L'istruzione in cui viene sospesa l'esecuzione del debugger e app è indicato dalla freccia gialla. La riga con la parentesi graffa aperta (`{`) dopo il `doWork` dichiarazione di funzione non è stata ancora eseguita.

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Se si dispone di un punto di interruzione in un ciclo o una ricorsione, o se si dispone di molti punti di interruzione che spesso un'istruzione alla volta, utilizzare un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per assicurarsi che il codice venga sospeso solo quando vengono soddisfatte specifiche condizioni. Questo consente di risparmiare tempo e possa inoltre semplificare il debug di problemi che sono difficili da riprodurre.

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger di continuare. Viene illustrato un comando di spostamento di codice utile che è stato introdotto in Visual Studio 2017.

Mentre nel punto di interruzione in sospeso, passare il mouse sull'istruzione `return c2` fino a quando il verde **esecuzione fare clic su** pulsante ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png) viene visualizzata e quindi premere il **esecuzione fare clic su** pulsante.

![Esecuzione di fare clic su](../debugger/media/dbg-qs-run-to-click-aspnet.png)

L'applicazione continua l'esecuzione e si sofferma sulla riga di codice in cui si fa clic sul pulsante.

Comandi di tasti comuni utilizzati per eseguire il codice includono **F10** e **F11**. Per altre istruzioni dettagliate, vedere il [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Controllare le variabili in un suggerimento dati

1. Nella riga corrente di codice (contrassegnati con il puntatore di esecuzione giallo), passare il mouse su di `c2` oggetto con il mouse per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Il suggerimento dati mostra il valore corrente di `c2` variabile e consente di controllare le relative proprietà. Durante il debug, se viene visualizzato un valore che non si prevede che, probabilmente è un bug nelle righe precedenti o chiamate di codice. 

2. Espandere il suggerimento dati per esaminare i valori correnti delle proprietà di `c2` oggetto.

3. Se si desidera bloccare il suggerimento dati, in modo che è possibile continuare a visualizzare il valore di `c2` durante l'esecuzione di codice, fare clic sull'icona di piccole dimensioni pin. (È possibile spostare il suggerimento dati bloccato in una posizione comoda).

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se si rileva una modifica che si desidera testare nel codice durante l'esecuzione di una sessione di debug, è possibile farlo, troppo.

1. Nel `OnGet` (metodo), fare clic su nella seconda istanza di `result.First.Value` e modificare `result.First.Value` a `result.Last.Value`.

1. Premere **F10** (o **Debug > Esegui istruzione/routine**) poche volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "modifica e continuazione")

    **F10** sposta in avanti l'istruzione debugger uno alla volta, ma i passaggi su funzioni anziché eseguire un'istruzione avervi (il codice che viene comunque eseguita).

Per ulteriori informazioni sull'utilizzo di modifica e continuazione e alle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger vengono forniti collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
