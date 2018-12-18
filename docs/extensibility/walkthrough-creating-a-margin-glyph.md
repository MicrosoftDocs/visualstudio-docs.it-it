---
title: "Procedura dettagliata: Creazione di un'icona di margine | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811985ef45fb43b08b771f2bc417a512c290726c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Procedura dettagliata: Creazione di un'icona di margine
È possibile personalizzare l'aspetto dei margini di editor utilizzando le estensioni di editor personalizzato. Questa procedura dettagliata inserisce un'icona personalizzata sul margine indicatore ogni volta che viene visualizzata la parola "attività" in un commento del codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `TodoGlyphTest`.  
  
2.  Aggiungere un elemento di progetto di classificatore Editor. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="defining-the-glyph"></a>Definire il glifo  
 Definire un glifo implementando il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaccia.  
  
#### <a name="to-define-the-glyph"></a>Per definire il glifo  
  
1.  Aggiungere un file di classe e assegnargli il nome `TodoGlyphFactory`.  
  
2.  Aggiungere quanto segue usando dichiarazioni.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Aggiungere una classe denominata `TodoGlyphFactory` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Aggiungere un campo privato che definisce le dimensioni dell'icona.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementare `GenerateGlyph` definendo l'elemento dell'interfaccia utente di glifo. `TodoTag` è definito più avanti in questa procedura dettagliata.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Esportazione di questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di VsTextMarker dopo un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodo creando il `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definizione di un Tag delle attività e Tagger  
 Definire la relazione tra l'elemento dell'interfaccia utente definiti nei passaggi precedenti e il margine indicatore creando un tipo di tag e tagger e esportarlo utilizzando un provider di tagger.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag delle attività e tagger  
  
1.  Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger`.  
  
2.  Aggiungere i seguenti.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Aggiungere una classe denominata `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Per il `TodoTagger` (classe), aggiungere campi privati per un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare nella classificazione si estende.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Aggiungere un costruttore che imposta la funzione di classificazione.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo individuando tutti la classificazione si estende i cui nomi includono la parola "comment" e il cui testo include il testo di ricerca. Ogni volta che il testo di ricerca viene trovato, produrre un nuovo indietro <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Dichiarare un `TagsChanged` evento.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Aggiungere una classe denominata `TodoTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importazione di <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo creando il `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest  
  
1.  Compilare la soluzione.  
  
2.  Premere F5 per eseguire il progetto. Viene creata un'istanza di una seconda istanza di Visual Studio.  
  
3.  Assicurarsi che venga visualizzato il margine indicatore. (Nel **strumenti** menu, fare clic su **opzioni**. Scegliere il **Editor di testo** pagina, assicurarsi che **margine indicatore** è selezionata.)  
  
4.  Aprire un file di codice che contiene i commenti. Aggiungere la parola "attività" per una delle sezioni di commento.  
  
5.  Nel margine indicatore a sinistra della finestra del codice, verrà visualizzato un cerchio blu chiaro con un contorno blu scuro.