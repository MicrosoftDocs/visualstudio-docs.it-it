---
title: SDK del visualizzatore di concorrenza | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f3745e863a94c0e2b899da0bf9d81589570c6ac0
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="concurrency-visualizer-sdk"></a>SDK del visualizzatore di concorrenza
Con l'SDK del visualizzatore di concorrenza è possibile instrumentare il codice sorgente in modo che nel visualizzatore di concorrenza siano visualizzate informazioni aggiuntive. È possibile associare i dati aggiuntivi a fasi ed eventi nel codice. Queste visualizzazioni aggiuntive sono note come *marcatori*.  Per una procedura dettagliata introduttiva, vedere [Introducing the Concurrency Visualizer SDK](http://go.microsoft.com/fwlink/?LinkId=235405).(Introduzione all'SDK del visualizzatore di concorrenza).  
  
## <a name="properties"></a>Proprietà  
 Flag, span e messaggi hanno due proprietà: categoria e importanza. Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) è possibile usare queste proprietà per filtrare il set di marcatori visualizzati. Queste proprietà influiscono anche sulla rappresentazione visiva dei marcatori. Ad esempio, l'importanza è rappresentata dalla dimensione dei flag, mentre il colore viene usato per indicare la categoria.  
  
## <a name="basic-usage"></a>Utilizzo di base  
 Il visualizzatore di concorrenza espone un provider predefinito che è possibile usare per generare i marcatori. Il provider è già registrato nel visualizzatore di concorrenza e non è necessario eseguire altre operazioni per visualizzare i marcatori nell'interfaccia utente.  
  
### <a name="c-and-visual-basic"></a>C# e Visual Basic  
 In C#, Visual basic e altro codice gestito usare il provider predefinito chiamando <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Espone le quattro funzioni per la generazione di marcatori: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> e <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Sono disponibili più overload per queste funzioni, a seconda che si voglia o meno usare le impostazioni predefinite per le proprietà.  L'overload più semplice accetta solo un parametro di stringa che specifica la descrizione dell'evento. La descrizione viene visualizzata nei rapporti del visualizzatore di concorrenza.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Per aggiungere un SDK a un progetto C# o Visual Basic  
  
1.  Nella barra dei menu scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.  
  
2.  Scegliere il progetto in cui si vuole aggiungere l'SDK e selezionare il pulsante **Aggiungi SDK al progetto selezionato**.  
  
3.  Aggiungere un'istruzione imports o using al codice.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 In C++ creare un oggetto [classe marker_series](../profiling/marker-series-class.md) e usarlo per chiamare le funzioni.  La classe `marker_series` espone tre funzioni per la generazione di indicatori: [marker_series::write_flag Method](../profiling/marker-series-write-flag-method.md), [marker_series::write_message Method](../profiling/marker-series-write-message-method.md) e [marker_series::write_alert Method](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Per aggiungere un SDK a un progetto C++ o C  
  
1.  Nella barra dei menu scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.  
  
2.  Scegliere il progetto in cui si vuole aggiungere l'SDK e selezionare il pulsante **Aggiungi SDK al progetto selezionato**.  
  
3.  Per C++, includere `cvmarkersobj.h`. Per C, includere `cvmarkers.h`.  
  
4.  Aggiungere un'istruzione using al codice.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Creare un oggetto `marker_series` e passarlo al costruttore `span`.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Utilizzo personalizzato  
 Per gli scenari avanzati, l'SDK del visualizzatore di concorrenza espone maggiore controllo.  A scenari più avanzati sono associati due concetti principali: provider marcatori e serie di marcatori. I provider marcatori sono provider ETW diversi, ognuno dei quali ha un GUID specifico. Le serie di marcatori sono canali di eventi seriali generati da un provider, che possono essere usate per organizzare gli eventi generati da un provider marcatori.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Per usare un nuovo provider marcatori in un progetto C# o Visual Basic  
  
1.  Creare un oggetto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Il costruttore accetta un GUID.  
  
2.  Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) del visualizzatore di concorrenza.  Selezionare la scheda **Marcatori** e selezionare il pulsante **Aggiungi nuovo provider**. Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) immettere il GUID usato per creare il provider e una descrizione del provider.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Per usare un nuovo provider marcatori in un progetto C++ o C  
  
1.  Usare la funzione `CvInitProvider` per inizializzare un PCV_PROVIDER.  Il costruttore accetta un GUID* e PCV_PROVIDER*\*.  
  
2.  Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Selezionare la scheda **Marcatori** e selezionare il pulsante **Aggiungi nuovo provider**. Nella finestra di dialogo immettere il GUID usato per creare il provider e una descrizione del provider.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Per usare una serie di marcatori in un progetto C# o Visual Basic  
  
1.  Per usare un nuova serie <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, è necessario prima crearla tramite un oggetto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>. A questo punto è possibile generare gli eventi marcatori direttamente dalla nuova serie.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Per usare una serie di marcatori in un progetto C++  
  
1.  Creare un oggetto `marker_series`.  Gli eventi possono essere generati da questa serie nuova.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Per usare una serie di marcatori in un progetto C  
  
1.  Usare la funzione `CvCreateMarkerSeries` per creare PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Riferimento alla libreria C++](../profiling/cpp-library-reference.md)|Viene descritta l'API del visualizzatore di concorrenza per C++.|  
|[Riferimento alla libreria C](../profiling/c-library-reference.md)|Viene descritta l'API del visualizzatore di concorrenza per C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Viene descritta l'API del visualizzatore di concorrenza per il codice gestito.|  
|[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)|Informazioni di riferimento sulle visualizzazioni e sui rapporti dei file di dati di profilatura che sono generati tramite il metodo di concorrenza e che includono dati di esecuzione thread.|