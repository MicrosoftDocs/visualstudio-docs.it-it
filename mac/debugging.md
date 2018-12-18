---
title: Debug con Xamarin | Microsoft Docs
description: "Il debug è una parte comune e necessaria della programmazione. In quanto IDE completo, Visual Studio per Mac contiene un intero gruppo di funzionalità per semplificare il debug. Dal debug sicuro alla visualizzazione dei dati, questo articolo descrive come sfruttare tutte le potenzialità del debug in Visual Studio per Mac."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 6d85c318b60e065be86d242bf3199b3716c59ada
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-with-xamarin"></a>Debug con Xamarin


Visual Studio per Mac ha un debugger nativo che offre supporto per il debug per applicazioni Xamarin.iOS, Xamarin.Mac e Xamarin.Android.
Visual Studio per Mac usa il [*debugger Mono Soft*](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), implementato nel runtime di Mono, per eseguire il debug di codice gestito in tutte le piattaforme.

## <a name="the-debugger"></a>Debugger

Visual Studio per Mac usa il debugger Mono Soft per eseguire il debug di codice gestito (C# r F#) in tutte le applicazioni Xamarin. Il debugger Mono Soft è diverso dai normali debugger in quanto è un debugger cooperativo integrato nel runtime di Mono. Il codice generato e il runtime di Mono cooperano con l'IDE per fornire l'esperienza di debug. Il runtime di Mono espone la funzionalità di debug tramite un protocollo di rete, su cui è possibile leggere altre informazioni nella [documentazione di Mono](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).


I debugger di tipo hard, come [LLDB]( http://lldb.llvm.org/index.html) o [GDB]( https://www.gnu.org/software/gdb/), controllano un programma in modo invisibile e senza la cooperazione del programma stesso, ma possono essere utili per il debug di applicazioni Xamarin quando è necessario eseguire il debug di codice iOS o Android nativo.

## <a name="using-the-debugger"></a>Uso del debugger

Per avviare il debug di qualsiasi applicazione, assicurarsi sempre che la configurazione sia impostata su **Debug**. La configurazione di debug offre un utile set di strumenti per il supporto del debug, come l'impostazione di punti di interruzione, l'uso di visualizzatori di dati e la visualizzazione dello stack di chiamate:

![Configurazione di debug](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Impostazione di un punto di interruzione

Per impostare un punto di interruzione nell'IDE, fare clic sull'area del margine nell'editor, accanto al numero di riga del codice in cui si vuole applicare l'interruzione:

![Impostazione di un punto di interruzione nel margine](media/debugging-image0.png)


È possibile visualizzare tutti i punti di interruzione impostati nel codice passando al **riquadro Punti di interruzione**:

![Elenco dei punti di interruzione](media/debugging-image0a.png)


## <a name="start-debugging"></a>Avvia debug

Per avviare il debug, selezionare il dispositivo di destinazione o l'emulatore o un altro strumento simile nell'IDE:

![Selezionare il dispositivo di destinazione](media/debugging-image1.png)

Distribuire quindi l'applicazione premendo il pulsante **Esegui** o **Comando+INVIO**. Quando si raggiunge un punto di interruzione, il codice viene evidenziato in giallo:

![Evidenziazione che indica il raggiungimento di un punto di interruzione](media/debugging-image2.png)

A questo punto, è possibile usare strumenti di debug, come quello usato per esaminare i valori degli oggetti, per ottenere altre informazioni su quello che accade nel codice:

![Visualizzazioni di debug](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Punti di interruzione condizionali

È anche possibile impostare regole che determinano i casi in cui deve essere presente un punto di interruzione, ovvero aggiungendo un *punto di interruzione condizionale*. Per impostare un punto di interruzione condizionale, accedere alla **finestra Proprietà punto di interruzione** in uno dei due modi seguenti:


* Per aggiungere un nuovo punto di interruzione condizionale, fare clic con il pulsante destro del mouse sul margine dell'editor, a sinistra del numero di riga per il codice in cui si vuole impostare il punto di interruzione, e quindi scegliere Nuovo punto di interruzione:


 ![Menu di scelta rapida Punto di interruzione](media/debugging-image4.png)

* Per aggiungere una condizione a un punto di interruzione, fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Proprietà punto di interruzione** oppure selezionare il pulsante Modifica punto di interruzione, mostrato di seguito, nel **riquadro Punti di interruzione**:


 ![Modifica del punto di interruzione esistente nel riquadro Punti di interruzione](media/debugging-image5.png)


È quindi possibile immettere la condizione in base alla quale deve essere aggiunto il punto di interruzione:

 ![Condizioni in Modifica punto di interruzione](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Esecuzione di codice istruzione per istruzione

Quando viene raggiunto un punto di interruzione, lo strumento di debug permette di ottenere il controllo sull'esecuzione del programma. Visual Studio per Mac visualizza quattro pulsanti, per eseguire e scorrere il codice. I pulsanti avranno l'aspetto seguente in Visual Studio per Mac:

 ![Pulsanti per scorrere il codice](media/debugging-image7.png)

Ecco i quattro pulsanti:

*   **Esegui**: avvia l'esecuzione del codice, fino al punto di interruzione successivo.
*   **Esegui istruzione/routine**: esegue la riga di codice successiva. Se la riga successiva è una chiamata di funzione, il pulsante esegue la funzione e si ferma alla riga di codice successiva, *dopo* la funzione.
*   **Esegui istruzione**: anche questo pulsante esegue la riga di codice successiva. Se la riga successiva è una chiamata di funzione, il pulsante si ferma alla prima riga della funzione, permettendo di continuare a eseguire il debug della funzione riga per riga. Se la riga successiva non è una funzione, il pulsante si comporta come il pulsante Esegui istruzione/routine.
*   **Esci da istruzione/routine**: torna alla riga in cui è stata chiamata la funzione corrente.


## <a name="debugging-monos-class-libraries"></a>Debug di librerie di classi di Mono
I prodotti Xamarin vengono forniti con il codice sorgente per le librerie di classi di Mono, che può essere usato per eseguire istruzioni passo a passo dal debugger ed esaminare il funzionamento sottostante.

Poiché questa funzionalità usa più memoria durante il debug, è disattivata per impostazione predefinita.

Per abilitare questa funzionalità, passare a **Visual Studio per Mac > Preferenze > Debugger** e assicurarsi che l'opzione **Esegui solo il debug del codice del progetto senza eseguire l'istruzione nel codice del framework**. sia **deselezionata**, come mostrato di seguito:

 ![Opzione Esegui solo il debug del codice del progetto senza eseguire l'istruzione nel codice del framework](media/debugging-image8.png)
