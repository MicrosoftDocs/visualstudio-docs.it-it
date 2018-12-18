---
title: 'Procedura dettagliata: Visualizzazione le parentesi graffe corrispondenti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3dde61c10d0a8c9fc5578b02cc713f648409cbf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>Procedura dettagliata: Visualizzazione di parentesi graffe corrispondenti
È possibile implementare funzionalità basate sul linguaggio, come parentesi graffa corrispondente definendo le parentesi graffe che deve corrispondere e quindi aggiungere un tag dell'indicatore di testo le parentesi graffe corrispondenti quando il punto di inserimento si trova su una delle parentesi graffe. È possibile definire le parentesi graffe all'interno di una lingua, è possibile definire il tipo di estensione e il contenuto di nome file e applicare i tag per quel tipo o è possibile applicare i tag a un tipo di contenuto esistente (ad esempio "text"). La procedura dettagliata seguente viene illustrato come applicare i tag per il tipo di contenuto "text" corrispondenza parentesi graffe.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto di classificatore editor. Denominare la soluzione `BraceMatchingTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementazione di una parentesi graffa corrispondente Tagger  
 Per ottenere una parentesi graffa evidenziazione effetto analogo a quello che viene utilizzata in Visual Studio, è possibile implementare un tagger del tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Il codice seguente viene illustrato come definire il tagger per le coppie di parentesi graffa a qualsiasi livello di annidamento. In questo esempio, la parentesi graffa di coppie []. [] e {} sono definiti nel costruttore tagger, ma in un'implementazione del linguaggio completa le coppie di parentesi graffa pertinente deve essere definite nella specifica del linguaggio.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare una parentesi graffa corrispondente tagger  
  
1.  Aggiungere un file di classe e denominarlo corrispondenza parentesi graffe.  
  
2.  Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Aggiungere le proprietà per la visualizzazione del testo, il buffer di origine e il punto dello snapshot corrente e anche un set di coppie di parentesi graffa.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Nel costruttore tagger, impostare le proprietà e sottoscrivere gli eventi di modifica della visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In questo esempio, a scopo illustrativo, le coppie corrispondenti vengono definite anche nel costruttore.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Come parte di <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  I gestori eventi aggiornano la posizione corrente del cursore del `CurrentChar` proprietà e generare l'evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo per la corrispondenza parentesi graffe uno quando il carattere corrente è una parentesi graffa di apertura o quando il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa di apertura e uno per la parentesi graffa di chiusura.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. I seguenti metodi privati trovare la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo consente di trovare il carattere di chiuso che corrisponda al carattere aperto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Il seguente metodo helper trovato il carattere aperto che corrisponde a un carattere di chiuso:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementazione di una parentesi graffa corrispondente Provider di Tagger  
 Oltre a implementare un tagger, è anche necessario implementare ed esportare un provider di tagger. In questo caso, il tipo di contenuto del provider è "text". Ciò significa che corrispondenza delle parentesi graffe verrà visualizzati tutti i tipi di file di testo, ma che un'implementazione completa potrebbe applicarsi parentesi graffa corrispondente solo a un tipo di contenuto specifico.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Per implementare un provider di tagger parentesi graffa corrispondente  
  
1.  Dichiarare che eredita da un provider di tagger <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, denominarla BraceMatchingTaggerProvider e l'esportazione con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di un BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare la soluzione BraceMatchingTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include parentesi graffe corrispondenti.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Quando si posiziona il punto di inserimento prima di una parentesi graffa di apertura, dovrebbe essere evidenziata sia la parentesi graffa e la corrispondente parentesi graffa di chiusura. Quando si posiziona il cursore subito dopo la parentesi graffa di chiusura, dovrebbe essere evidenziata sia la parentesi graffa e la parentesi graffa di apertura corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)