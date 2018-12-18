---
title: 'Procedura dettagliata: Creazione del componente aggiuntivo VSTO prima per il progetto | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e1b768a8d812d3a4c0222bbb3e762c0f5046f56
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project
  Questa procedura dettagliata illustra come creare un componente aggiuntivo VSTO per Microsoft Office Project. Le funzionalità create in questo tipo di soluzione sono disponibili per l'applicazione, indipendentemente dai progetti aperti. Per ulteriori informazioni, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di componente aggiuntivo VSTO di Project.  
  
-   Scrittura di codice che usa il modello a oggetti di Project per aggiungere un'attività a un nuovo progetto.  
  
-   Creazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] o [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creazione del progetto  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>Per creare un nuovo progetto in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.  
  
4.  Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .  
  
5.  Nell'elenco dei modelli di progetto selezionare **Componente aggiuntivo per Project 2010** o **Componente aggiuntivo per Project 2013**.  
  
6.  Nella casella **Nome** digitare **FirstProjectAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto **FirstProjectAddIn** e apre il file di codice **ThisAddIn** nell'editor.  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>Scrittura di codice che aggiunge una nuova attività a un progetto  
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Project per aggiungere una nuova attività a un progetto. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn` . Questa classe fornisce un punto di ingresso per il codice e consente di accedere al modello a oggetti di Project. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown` . Questi gestori eventi vengono chiamati quando Project carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato. Per altre informazioni, vedere [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-task-to-a-new-project"></a>Per aggiungere un'attività a un nuovo progetto  
  
1.  Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice definisce un gestore eventi per l'evento NewProject della classe Microsoft.Office.Interop.MSProject.Application.  
  
     Quando l'utente crea un nuovo progetto, questo gestore eventi aggiunge un'attività al progetto.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 Per modificare il progetto, in questo esempio di codice vengono usati gli oggetti seguenti:  
  
-   Il campo `Application` della classe `ThisAddIn` . Il `Application` campo restituisce un oggetto Microsoft.Office.Interop.MSProject.Application, che rappresenta l'istanza corrente del progetto.  
  
-   Il `pj` parametro del gestore eventi per l'evento NewProject. Il `pj` parametro è un oggetto Microsoft.Office.Interop.MSProject.Project, che rappresenta il progetto. Per altre informazioni, vedere [Project Solutions](../vsto/project-solutions.md).  
  
1.  Se si usa C#, aggiungere il seguente codice al gestore eventi `ThisAddIn_Startup` . Questo codice si connette il `Application_Newproject` gestore eventi all'evento NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>Test del progetto  
 Quando si compila e si esegue il progetto, verificare che la nuova attività venga visualizzata nel progetto risultante.  
  
#### <a name="to-test-the-project"></a>Per testare il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto. Microsoft Project viene avviato e viene aperto automaticamente un nuovo progetto vuoto.  
  
     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Visual Studio crea anche un set di voci del Registro di sistema che permettono a Project di individuare e caricare il componente aggiuntivo VSTO e configura le impostazioni di sicurezza nel computer di sviluppo per consentire l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Panoramica del processo di compilazione delle soluzioni Office](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Verificare che nel progetto vuoto sia stata aggiunta una nuova attività.  
  
3.  Verificare che nel campo **Task Name** dell'attività sia visualizzato il testo seguente.  
  
     **This text was added by using code.**  
  
4.  Chiudere Microsoft Project.  
  
## <a name="cleaning-up-the-project"></a>Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si apre Microsoft Project nel computer di sviluppo.  
  
#### <a name="to-clean-up-your-project"></a>Per pulire il progetto  
  
1.  In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver creato un componente aggiuntivo VSTO di base per Project, vedere gli argomenti seguenti per altre informazioni su come sviluppare componenti aggiuntivi VSTO:  
  
-   Attività di programmazione generali che è possibile eseguire usando i componenti aggiuntivi VSTO per Project: [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Uso del modello a oggetti di Project: [Project Solutions](../vsto/project-solutions.md).  
  
-   Compilazione e debug di componenti aggiuntivi VSTO per Project: [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di componenti aggiuntivi VSTO per Project: [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Soluzioni Project](../vsto/project-solutions.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  