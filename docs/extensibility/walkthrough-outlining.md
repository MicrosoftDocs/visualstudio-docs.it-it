---
title: 'Procedura dettagliata: Struttura | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15dd5f0121fca86a38631bf775ec25d4428632e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: struttura
È possibile implementare una funzionalità basata su linguaggio, ad esempio definendo i tipi di aree di testo che si desidera espandere o comprimere la struttura. È possibile definire le aree nel contesto di un servizio di linguaggio, è possibile definire il tipo di estensione e il contenuto di nome file e applicare la definizione dell'area a solo a quel tipo o è possibile applicare le definizioni di area per un tipo di contenuto esistente (ad esempio "text"). Questa procedura dettagliata viene illustrato come definire e visualizzare le aree della struttura.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto VSIX. Denominare la soluzione `OutlineRegionTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementazione di un Tagger struttura  
 Le aree della struttura sono contrassegnate da un tipo di tag (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Questo tag fornisce la struttura di comportamento standard. L'area indicato può essere espansi o compressi. L'area strutturato è contrassegnato da un segno più, se è compresso o un segno di sottrazione viene espanso, se l'area espansa è delimitata da una linea verticale.  
  
 La procedura seguente viene illustrato come definire un tagger che crea le aree della struttura per tutte le aree sono delimitate da "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Per implementare un tagger struttura  
  
1.  Aggiungere un file di classe e assegnargli il nome `OutliningTagger`.  
  
2.  Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Creare una classe denominata `OutliningTagger`, e che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Aggiungere alcuni campi per tenere traccia il buffer di testo e lo snapshot e per accumulare i set di righe che devono essere contrassegnate come aree della struttura. Questo codice include un elenco di oggetti area (da definire in un secondo momento) che rappresentano le aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Aggiungere un costruttore tagger che inizializza i campi, analizza il buffer e aggiunge un gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> si estende su metodo, che crea un'istanza del tag. In questo esempio si presuppone che gli intervalli nel <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passato al metodo sono contigui, anche se questo non può essere sempre il caso. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Dichiarare un `TagsChanged` gestore dell'evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Aggiungere un `BufferChanged` gestore dell'evento che risponde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventi analizzando il buffer di testo.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Aggiungere un metodo che analizza il buffer. L'esempio riportato di seguito è solo a scopo illustrativo. Viene analizzata in modo sincrono il buffer in aree della struttura nidificate.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Il seguente metodo helper Ottiene un intero che rappresenta il livello di struttura, in modo che la coppia di parentesi graffa di sinistra è 1.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Il seguente metodo helper traduce un'area (definita più avanti in questo argomento) in un oggetto SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Il codice seguente è solo a scopo illustrativo. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dall'inizio di un'area della struttura e un riferimento all'area del padre (se presente). In questo modo, il parser impostare annidati aree della struttura. Una classe derivata di area contiene un riferimento al numero di riga della fine di un'area della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementazione di un Provider di Tagger  
 È necessario esportare un provider di tagger del tagger. Il provider di tagger crea un `OutliningTagger` per un buffer del tipo di contenuto "text", o altri restituisce un `OutliningTagger` se il buffer contiene già uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Per implementare un provider di tagger  
  
1.  Creare una classe denominata `OutliningTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ed esportarlo con gli attributi ContentType e TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo aggiungendo un `OutliningTagger` a quelle del buffer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo. Digitare testo che include sia la parentesi graffa di apertura e la parentesi graffa di chiusura.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Deve essere presente un'area della struttura che include sia le parentesi graffe. Dovrebbe essere possibile fare clic sul segno meno a sinistra della parentesi graffa di apertura per comprimere l'area della struttura. Quando l'area è compresso, il simbolo di puntini di sospensione (...) deve apparire a sinistra dell'area compressa e una finestra popup contenente il testo **passa il mouse testo** deve essere visualizzato quando si sposta il puntatore del mouse sui puntini di sospensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)