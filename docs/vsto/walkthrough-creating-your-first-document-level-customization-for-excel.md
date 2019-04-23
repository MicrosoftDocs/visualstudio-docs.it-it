---
title: 'Procedura dettagliata: Creare una personalizzazione a livello di documento per Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81020496c1e80718d1aa0995791762d55ef70a76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104499"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Procedura dettagliata: Creare una personalizzazione a livello di documento per Excel
  Questa procedura dettagliata introduttiva mostra come creare una personalizzazione a livello di documento per Microsoft Office Excel. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre una cartella di lavoro specifica. Una personalizzazione a livello di documento non può essere usata per apportare modifiche a un'intera applicazione, ad esempio per visualizzare una nuova scheda della barra multifunzione quando si apre una cartella di lavoro qualsiasi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto cartella di lavoro di Excel.

- Aggiunta di testo a un foglio di lavoro ospitato nella finestra di progettazione di Visual Studio.

- Scrittura di codice che usa il modello a oggetti di Excel per aggiungere testo al foglio di lavoro personalizzato quando quest'ultimo viene aperta.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto completato per rimuovere dal computer di sviluppo le impostazioni di sicurezza e i file di compilazione non necessari.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Per creare un nuovo progetto cartella di lavoro di Excel in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

5. Nell'elenco dei modelli di progetto scegliere un progetto di componente aggiuntivo VSTO di Excel.

6. Nel **Name** , digitare **FirstWorkbookCustomization**.

7. Fare clic su **OK**.

    Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

8. Selezionare **creare un nuovo documento**, fare clic su **OK**.

   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea il **FirstWorkbookCustomization** del progetto e aggiunge i file seguenti al progetto.

   - *FirstWorkbookCustomization*xlsx - rappresenta la cartella di lavoro di Excel nel progetto. Contiene tutti i fogli di lavoro e i grafici.

   - Sheet1 (*vb* file per Visual Basic o *cs* file per Visual c#)-un foglio di lavoro che fornisce l'area di progettazione e il codice per il primo foglio della cartella di lavoro. Per altre informazioni, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).

   - Sheet2 (*vb* file per Visual Basic o *cs* file per Visual c#)-un foglio di lavoro che fornisce l'area di progettazione e il codice per il secondo foglio della cartella di lavoro.

   - Sheet3 (*vb* file per Visual Basic o *cs* file per Visual c#)-un foglio di lavoro che fornisce l'area di progettazione e il codice per il terzo foglio della cartella di lavoro.

   - ThisWorkbook (*vb* file per Visual Basic o *cs* file per Visual c#)-contiene l'area di progettazione e il codice per le personalizzazioni a livello di cartella di lavoro. Per altre informazioni, vedere [elemento host Workbook](../vsto/workbook-host-item.md).

     Il file di codice Sheet1 viene aperto automaticamente nella finestra di progettazione.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Chiudere e riaprire i fogli di lavoro nella finestra di progettazione
 Se mentre si sviluppa il progetto si chiude intenzionalmente o accidentalmente una cartella di lavoro o un foglio di lavoro nella finestra di progettazione, è possibile riaprirlo.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Per chiudere e riaprire un foglio di lavoro nella finestra di progettazione

1. Chiudere la cartella di lavoro facendo il **Chiudi** pulsante (X) della finestra di progettazione.

2. Nella **Esplora soluzioni**, fare doppio clic il **Sheet1** file di codice e fare clic su **Progettazione viste**.

     \- oppure -

     Nelle **Esplora soluzioni**, fare doppio clic il **Sheet1** file di codice.

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Aggiungere testo a un foglio di lavoro nella finestra di progettazione
 È possibile progettare l'interfaccia utente della personalizzazione modificando il foglio di lavoro aperto nella finestra di progettazione. Ad esempio, è possibile aggiungere testo alle celle, applicare formule o aggiungere controlli di Excel. Per altre informazioni su come usare la finestra di progettazione, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Per aggiungere testo a un foglio di lavoro mediante la finestra di progettazione

1. Nel foglio di lavoro è aperta nella finestra di progettazione, selezionare celle **A1**, quindi digitare il testo seguente.

     **Questo testo è stato aggiunto usando la finestra di progettazione.**

> [!WARNING]
>  Se si aggiunge questa riga di testo alla cella **A2**, verrà sovrascritta da altro codice in questo esempio.

## <a name="add-text-to-a-worksheet-programmatically"></a>Aggiungere testo a un foglio di lavoro a livello di codice
 Aggiungere quindi codice al file di codice Sheet1. Il nuovo codice usa il modello a oggetti di Excel per aggiungere nella cartella di lavoro una seconda riga di testo. Per impostazione predefinita, il file di codice Sheet1 contiene il seguente codice generato:

- Una definizione parziale della classe `Sheet1`, che rappresenta il modello di programmazione del foglio di lavoro e consente di accedere al modello a oggetti di Excel. Per altre informazioni, [elemento host Worksheet](../vsto/worksheet-host-item.md) e [Cenni preliminari sul modello a oggetti di Word](../vsto/word-object-model-overview.md). Il resto della classe `Sheet1` viene definito in un file di codice nascosto che l'utente non deve modificare.

- I gestori eventi `Sheet1_Startup` e `Sheet1_Shutdown` . Questi gestori eventi vengono chiamati quando Excel carica e scarica la personalizzazione. Usare questi gestori eventi per inizializzare la personalizzazione quando viene caricata e per eseguire la pulizia delle risorse usate dalla personalizzazione quando viene scaricata. Per altre informazioni, vedere [gli eventi nei progetti di Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Per aggiungere al foglio di lavoro una seconda riga di codice mediante codice

1. Nelle **Esplora soluzioni**, fare doppio clic su **Sheet1**, quindi fare clic su **Visualizza codice**.

     Il file di codice verrà aperto in Visual Studio.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Quando viene aperto il foglio Sheet1, questo codice aggiunge una seconda riga di testo al foglio di lavoro.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Il progetto di test

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si compila il progetto, il codice viene compilato in un assembly associato alla cartella di lavoro. Visual Studio inserisce una copia della cartella di lavoro e l'assembly nella cartella dell'output di compilazione del progetto e configura le impostazioni di sicurezza nel computer di sviluppo in modo da consentire l'esecuzione della personalizzazione. Per altre informazioni, vedere [soluzioni Office compilare](../vsto/building-office-solutions.md).

2. Nella cartella di lavoro verificare che sia visualizzato il testo seguente.

     **Questo testo è stato aggiunto usando la finestra di progettazione.**

     **This text was added by using code.**

3. Chiudere la cartella di lavoro.

## <a name="clean-up-the-project"></a>Pulire il progetto
 Al termine dello sviluppo di un progetto, è necessario rimuovere le impostazioni di sicurezza e i file contenuti nella cartella dell'output di compilazione creati dal processo di compilazione.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi
 Dopo aver creato questa personalizzazione di base a livello di documento per Excel, per approfondire le proprie conoscenze sullo sviluppo di personalizzazioni è possibile consultare gli argomenti seguenti:

- Attività di programmazione generali che è possibile eseguire nelle personalizzazioni a livello di documento: [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

- Attività di programmazione specifiche per le personalizzazioni a livello di documento per Excel: [Soluzioni Excel](../vsto/excel-solutions.md).

- Usando il modello a oggetti di Excel: [Panoramica del modello a oggetti Excel](../vsto/excel-object-model-overview.md).

- Personalizzazione dell'interfaccia utente di Excel, ad esempio, aggiungendo una scheda personalizzata alla barra multifunzione o creando un riquadro azioni personalizzato: [Personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).

- Usando oggetti estesi di Excel forniti dagli strumenti di sviluppo per Office in Visual Studio per eseguire attività che non sono possibili utilizzando il modello a oggetti di Excel (ad esempio, hosting di controlli gestiti nei documenti e associazione di controlli di Excel ai dati usando i moduli di Windows modello di data binding): [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).

- Compilazione e debug di personalizzazioni a livello di documento per Excel: [Creazione di soluzioni Office](../vsto/building-office-solutions.md).

- Distribuzione di personalizzazioni a livello di documento per Excel: [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluzioni Excel](../vsto/excel-solutions.md)
- [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Creazione di soluzioni Office](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)
