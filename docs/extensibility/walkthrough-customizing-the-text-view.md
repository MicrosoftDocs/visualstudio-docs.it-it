---
title: 'Procedura dettagliata: Personalizzazione della visualizzazione di testo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ecbf5e3bed5ba506278f00b2b5b0b76f8f02850a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-customizing-the-text-view"></a>Procedura dettagliata: Personalizzazione della visualizzazione di testo
Modificando le proprietà seguenti nella mappa formato dell'editor, è possibile personalizzare una visualizzazione di testo:  
  
-   Margine indicatore  
  
-   Punto di inserimento  
  
-   Sovrascrittura del punto di inserimento  
  
-   Testo selezionato  
  
-   Testo selezionato inattivo (vale a dire testo selezionato che perde lo stato attivo)  
  
-   Lo spazio vuoto  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `ViewPropertyTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1.  Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.  
  
2.  Aggiungere il seguente `using` direttive:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Esportazione di questa classe con gli attributi seguenti:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>Per specificare il tipo di contenuto a cui si applica questo listener.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>Per specificare il ruolo del listener.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Questa classe, importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Modifica delle proprietà di visualizzazione  
  
1.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che le proprietà della vista vengono modificate quando viene aperta la visualizzazione. Per apportare la modifica, trovare il <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della vista a cui si desidera trovare. Quindi, modificare la proprietà appropriata nel dizionario risorse e impostare le proprietà. Le chiamate a batch il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodo prima di impostare le proprietà e quindi la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> dopo aver impostato le proprietà.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1.  Compilare la soluzione.  
  
     Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2.  Creare un file di testo e digitare alcune parole.  
  
    -   Il punto di inserimento deve essere magenta e il punto di inserimento di sovrascrittura deve essere turchese.  
  
    -   Il margine indicatore (a sinistra della visualizzazione di testo) deve essere una luce verde.  
  
3.  Selezionare il testo digitato. Il colore del testo selezionato deve essere chiaro rosa.  
  
4.  Mentre il testo è selezionato, fare clic all'esterno dell'intervallo di testo. Il colore del testo selezionato deve essere Rosa scuro.  
  
5.  Attivare lo spazio vuoto. (Nel **modifica** dal menu **avanzate** e quindi fare clic su **Mostra/Nascondi spazi**). Digitare il testo alcune schede. Le frecce rosse indicano che rappresentano le schede devono essere visualizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)