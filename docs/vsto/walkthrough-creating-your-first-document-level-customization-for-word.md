---
title: 'Procedura dettagliata: Creazione di una personalizzazione a livello di documento per Word | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bb85c10b2a66741bf0405d4a1313fb2343a708b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-word"></a>Procedura dettagliata: creazione di una personalizzazione a livello di documento per Word
  Questa procedura dettagliata introduttiva mostra come creare una personalizzazione a livello di documento per Microsoft Office Word. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre un documento specifico. Una personalizzazione a livello di documento non può essere usata per apportare modifiche a un'intera applicazione, ad esempio per visualizzare una nuova scheda della barra multifunzione quando si apre un documento qualsiasi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto relativo al documento di Word  
  
-   Aggiunta di testo al documento ospitato nella finestra di progettazione di Visual Studio.  
  
-   Scrittura di codice che usa il modello a oggetti di Word per aggiungere testo al documento personalizzato quando quest'ultimo viene aperto.  
  
-   Creazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto per rimuovere dal computer di sviluppo le impostazioni di sicurezza e i file di compilazione non necessari.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Creazione del progetto  
  
#### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Per creare un progetto di documento di Word in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.  
  
4.  Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .  
  
5.  Nell'elenco di modelli di progetto selezionare un progetto Documento VSTO di Word.  
  
6.  Nel **nome** digitare **FirstDocumentCustomization**.  
  
7.  Fare clic su **OK**.  
  
     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .  
  
8.  Selezionare **creare un nuovo documento**, fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea il **FirstDocumentCustomization** del progetto e aggiunge il **FirstDocumentCustomization** documenti e file di codice ThisDocument al progetto. Il **FirstDocumentCustomization** documento viene aperto automaticamente nella finestra di progettazione.  
  
## <a name="closing-and-reopening-the-document-in-the-designer"></a>Chiusura e riapertura del documento nella finestra di progettazione  
 Se mentre si sviluppa il progetto nella finestra di progettazione si chiude intenzionalmente o accidentalmente il documento, è possibile riaprirlo.  
  
#### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Per chiudere e riaprire il documento nella finestra di progettazione  
  
1.  Chiudere il documento facendo il **Chiudi** pulsante (X) della finestra di progettazione.  
  
2.  In **Esplora**, fare doppio clic su di **ThisDocument** file di codice e fare clic su **Visualizza finestra di progettazione**.  
  
     \- oppure -  
  
     In **Esplora**, fare doppio clic su di **ThisDocument** file di codice.  
  
## <a name="adding-text-to-the-document-in-the-designer"></a>Aggiunta di testo al documento nella finestra di progettazione  
 È possibile progettare l'interfaccia utente della personalizzazione modificando il documento che viene aperto nella finestra di progettazione. Ad esempio, è possibile aggiungere testo, tabelle o controlli Word. Per ulteriori informazioni su come usare la finestra di progettazione, vedere [progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Per aggiungere testo al documento con la finestra di progettazione  
  
1.  Nel documento aperto nella finestra di progettazione, digitare il testo seguente.  
  
     **Questo testo è stato aggiunto tramite la finestra di progettazione.**  
  
## <a name="adding-text-to-the-document-programmatically"></a>Aggiunta di testo al documento a livello di codice  
 Quindi, aggiungere codice al file di codice ThisDocument. Il nuovo codice usa il modello a oggetti di Word per aggiungere nel documento un secondo paragrafo di testo. Per impostazione predefinita, il file di codice ThisDocument contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisDocument`, che rappresenta il modello di programmazione del documento e consente di accedere al modello a oggetti di Word. Per ulteriori informazioni, vedere [elemento Host documento](../vsto/document-host-item.md) e [Panoramica del modello oggetto Word](../vsto/word-object-model-overview.md). Il resto della classe `ThisDocument` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisDocument_Startup` e `ThisDocument_Shutdown`. Questi gestori eventi vengono chiamati quando il documento viene aperto o chiuso. Possono essere usati per inizializzare la personalizzazione quando il documento viene aperto e per liberare le risorse usate dalla personalizzazione quando il documento viene chiuso. Per altre informazioni, vedere [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Per aggiungere nel documento un secondo paragrafo di testo usando il codice  
  
1.  In **Esplora**, fare doppio clic su **ThisDocument**, quindi fare clic su **Visualizza codice**.  
  
     Il file di codice verrà aperto in Visual Studio.  
  
2.  Sostituire il gestore eventi `ThisDocument_Startup` con il codice seguente. Quando il documento viene aperto, questo codice aggiunge un secondo paragrafo di testo al documento.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Questo codice usa il valore di indice 1 per accedere al primo paragrafo contenuto nella proprietà <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Anche se Visual Basic e Visual C# usano matrici in base 0, il limite inferiore di matrice della maggior parte delle raccolte del modello a oggetti di Word è 1. Per altre informazioni, vedere [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="testing-the-project"></a>Test del progetto  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere **F5** per compilare ed eseguire il progetto.  
  
     Quando si compila il progetto, il codice viene compilato in un assembly associato al documento. Visual Studio inserisce una copia del documento e l'assembly nella cartella dell'output di compilazione del progetto e configura le impostazioni di sicurezza nel computer di sviluppo in modo da consentire l'esecuzione della personalizzazione. Per ulteriori informazioni, vedere [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
2.  Nel documento, verificare che sia visualizzato il testo seguente.  
  
     **Questo testo è stato aggiunto tramite la finestra di progettazione.**  
  
     **This text was added by using code.**  
  
3.  Chiudere il documento.  
  
## <a name="cleaning-up-the-project"></a>Pulizia del progetto  
 Al termine dello sviluppo di un progetto, è necessario rimuovere le impostazioni di sicurezza e i file contenuti nella cartella dell'output di compilazione creati dal processo di compilazione.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo  
  
1.  In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver creato questa personalizzazione di base a livello di documento per Word, per approfondire le proprie conoscenze sullo sviluppo di personalizzazioni è possibile consultare gli argomenti seguenti:  
  
-   Attività di programmazione generale eseguibili nelle personalizzazioni a livello di documento: [programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
-   Attività di programmazione specifiche per le personalizzazioni a livello di documento per Word: [soluzioni Word](../vsto/word-solutions.md).  
  
-   Utilizzando il modello a oggetti di Word: [Panoramica del modello oggetto Word](../vsto/word-object-model-overview.md).  
  
-   Personalizzazione dell'interfaccia utente di Word, ad esempio, per l'aggiungendo una scheda personalizzata alla barra multifunzione o la creazione di un riquadro azioni personalizzato: [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
-   Utilizzo di oggetti estesi di Word forniti da soluzioni Office in Visual Studio per eseguire attività che non sono possibili utilizzando il modello a oggetti di Word (ad esempio, l'hosting di controlli gestiti nei documenti e associazione di controlli di Word ai dati utilizzando i dati di Windows Form modello di associazione): [automazione di Word utilizzando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Compilazione e debug di personalizzazioni a livello di documento per Word: [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di personalizzazioni a livello di documento per Word: [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sullo sviluppo di soluzioni di Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  