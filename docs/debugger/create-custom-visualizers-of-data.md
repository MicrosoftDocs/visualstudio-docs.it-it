---
title: Creazione di visualizzatori personalizzati dei dati | Documenti Microsoft
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 23985c56ba61e5a788232523611a48cfde902335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-visualizers-of-data"></a>Creazione di visualizzatori personalizzati dei dati
 I visualizzatori sono componenti del [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] l'interfaccia utente del debugger. Oggetto *Visualizzatore* crea una finestra di dialogo o un'altra interfaccia per visualizzare una variabile o un oggetto in modo appropriato per il tipo di dati. Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come apparirebbe in una finestra del browser; un visualizzatore di bitmap interpreta una struttura di bitmap e visualizza l'oggetto grafico da essa rappresentato. Alcuni visualizzatori consentono inoltre di modificare i dati.

 Il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] include sei visualizzatori standard. Si tratta di testo, HTML, XML e JSON visualizzatori, che funziona per gli oggetti stringa; il Visualizzatore dell'albero di WPF, per visualizzare le proprietà di un oggetto visual dell'albero di WPF; e il Visualizzatore di dataset, che può essere usato per gli oggetti DataSet, DataView e DataTable. In futuro è possibile che Microsoft Corporation renda disponibili ulteriori visualizzatori per il download, mentre altri potranno essere disponibili tramite terze parti e dalla community. È inoltre possibile scrivere visualizzatori personalizzati e installarli nel debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

 > [!NOTE]
 > Per creare un visualizzatore personalizzato per il codice nativo, vedere il [visualizzatore del Debugger nativo SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) esempio. In UWP e Windows 8. x le app, i visualizzatori personalizzati non sono supportati.

 Nel debugger, i visualizzatori sono rappresentati da un'icona di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore"). Quando viene visualizzata l'icona di lente di ingrandimento in una **suggerimento dati**, in una finestra del debugger, ad esempio il **espressioni di controllo** finestra o nel **controllo immediato** nella finestra di dialogo è possibile fare clic sulla lente di ingrandimento Selezionare un visualizzatore appropriato per il tipo di dati dell'oggetto corrispondente.

## <a name="overview-of-custom-visualizers"></a>Panoramica di visualizzatori personalizzati

È possibile scrivere un visualizzatore personalizzato per un oggetto di qualsiasi classe gestita, ad eccezione di <xref:System.Object> o <xref:System.Array>.  
  
 L'architettura di un visualizzatore del debugger è definita da due parti:  
  
-   Il *lato debugger* viene eseguito all'interno del debugger di Visual Studio. Il codice del lato debugger crea e visualizza l'interfaccia utente del visualizzatore.  
  
-   Il *lato oggetto del debug* viene eseguito all'interno del processo di debug in Visual Studio (il *oggetto del debug*).  
  
 L'oggetto dati che si desidera visualizzare, ad esempio un oggetto stringa, esiste nel processo dell'oggetto del debug. Di conseguenza, il lato oggetto del debug deve inviare l'oggetto dati al lato debugger, che può quindi visualizzarlo in un'interfaccia utente creata dallo sviluppatore.  
  
 Il lato debugger riceve questo oggetto dati da visualizzare da un *provider di oggetti* che implementa il <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaccia. Il lato oggetto del debug invia l'oggetto dati tramite il *origine oggetto*, che deriva da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Il provider di oggetti può inoltre inviare nuovamente i dati all'origine oggetto consentendo in tal modo di scrivere un visualizzatore che modifica e visualizza i dati. Il provider di oggetti può essere sottoposto a override per comunicare con l'analizzatore di espressioni e, di conseguenza, con l'origine oggetto.  
  
 L'oggetto del debug e il lato debugger comunicano tra loro tramite la classe <xref:System.IO.Stream>. Sono disponibili metodi che consentono di serializzare un oggetto dati in un oggetto <xref:System.IO.Stream> e deserializzare l'oggetto <xref:System.IO.Stream> in un oggetto dati.  
  
 Il codice dell'oggetto del debug viene specificato tramite l'attributo DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Per creare l'interfaccia utente del visualizzatore nel lato debugger, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ed eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia.  
  
 È possibile usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows Forms, finestre di dialogo e controlli nel visualizzatore.  
  
 Il supporto per i tipi generici è limitato. È possibile scrivere un visualizzatore per una destinazione di tipo generico solo quest'ultimo è di tipo aperto. Questa limitazione è identica a quella prevista quando si usa l'attributo `DebuggerTypeProxy`. Per informazioni dettagliate, vedere [utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Ai visualizzatori personalizzati possono essere associate considerazioni sulla sicurezza. Vedere [considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md).  
  
 Nelle procedure riportate di seguito vengono fornite informazioni generali sulle operazioni da effettuare per creare un visualizzatore. Per una spiegazione più dettagliata, vedere [procedura dettagliata: scrittura di un visualizzatore in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Per creare il lato debugger  
  
1.  Usare metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> per fornire l'oggetto visualizzato al lato debugger.  
  
2.  Creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia. Usare i metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows Forms, finestre di dialogo e controlli all'interno dell'interfaccia.  
  
4.  Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> per assegnare un visualizzatore (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Per creare il lato oggetto del debug  
  
1.  Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> per assegnare un visualizzatore (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) e un'origine oggetto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Se si omette l'origine oggetto, verrà usata un'origine predefinita.  
  
2.  Se si desidera che il visualizzatore sia in grado di modificare oggetti dati oltre a visualizzarli, eseguire l'override del metodo `TransferData` o `CreateReplacementObject` della classe <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>In questa sezione
  
 [Procedura dettagliata: scrittura di un visualizzatore in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Procedura dettagliata: scrittura di un visualizzatore in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)  
  
 [Procedura: Testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)