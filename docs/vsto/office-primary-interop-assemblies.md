---
title: "Assembly di interoperabilità primari di Office | Documenti Microsoft"
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
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 906100a572170f218a23b1887ab7fddee37251b9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="office-primary-interop-assemblies"></a>assembly di interoperabilità primari di Office
  Per usare le funzionalità di un'applicazione di Microsoft Office di un progetto di Office è necessario usare l'assembly di interoperabilità primario (PIA) per l'applicazione. L'assembly di interoperabilità primario consente l'interazione tra il codice gestito e il modello a oggetti basati su COM di un'applicazione di Microsoft Office.  
  
 Quando si crea un nuovo progetto di Office, Visual Studio aggiunge riferimenti agli assembly di interoperabilità primari che sono necessari per compilare il progetto. In alcuni scenari, può essere necessario aggiungere riferimenti agli assembly PIA (ad esempio, se si vuole usare una funzionalità di Microsoft Office Word in un progetto per Microsoft Office Excel).  
  
 Questo argomento descrive i seguenti aspetti dell'uso degli assembly di interoperabilità primari di Microsoft Office nei progetti di Office:  
  
-   [Separare gli assembly di interoperabilità primari per la compilazione e l'esecuzione di progetti](#separateassemblies)  
  
-   [Uso delle funzionalità di più applicazioni di Microsoft Office in un unico progetto](#usingfeatures)  
  
-   [Elenco completo di assembly di interoperabilità primari per applicazioni di Microsoft Office](#pialist)  
  
 Per altre informazioni sugli assembly di interoperabilità primari, vedere [Assembly di interoperabilità primari](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
##  <a name="separateassemblies"></a> Separate Primary Interop Assemblies for Building and Running Projects  
 Visual Studio usa diversi set di assembly di interoperabilità primari sul computer di sviluppo, che si trovano nei seguenti percorsi:  
  
-   Una cartella nella directory dei file di programma.  
  
     Queste copie degli assembly vengono usate durante la scrittura del codice e la compilazione dei progetti. Visual Studio installa automaticamente questi assembly.  
  
-   Global Assembly Cache.  
  
     Queste copie degli assembly vengono usate durante alcune attività di sviluppo, come l'esecuzione o il debug dei progetti. Visual Studio non installa né registra questi assembly: è necessario che l'utente operi autonomamente.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Assembly di interoperabilità primari nella directory dei file di programma  
 Quando si installa Visual Studio, gli assembly di interoperabilità primari vengono automaticamente installati in un percorso del file system, all'esterno della Global Assembly Cache. Quando si crea un nuovo progetto, Visual Studio aggiunge automaticamente al progetto riferimenti a queste copie degli assembly di interoperabilità primari. Visual Studio usa queste copie degli assembly di interoperabilità primari invece che degli assembly nella Global Assembly Cache, per risolvere i riferimenti ai tipi quando si sviluppa e si compila il progetto.  
  
 Queste copie degli assembly di interoperabilità primari contribuiscono a evitare diversi problemi di sviluppo che possono verificarsi in Visual Studio quando si registrano versioni differenti degli assembly nella Global Assembly Cache.  
  
 Visual Studio installa queste copie degli assembly di interoperabilità primari nei seguenti percorsi del computer di sviluppo:  
  
-   %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools per Office\PIA\Office14  
  
     (o %ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools per Office\PIA\Office14 nei sistemi operativi a 64 bit)  
  
-   %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools per Office\PIA\Office15  
  
     (o %ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools per Office\PIA\Office15 nei sistemi operativi a 64 bit)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Assembly di interoperabilità primari nella Global Assembly Cache  
 Per eseguire determinate attività di sviluppo, gli assembly di interoperabilità primari devono essere installati e registrati nella Global Assembly Cache sul computer di sviluppo. Di solito, gli assembly di interoperabilità primari vengono installati automaticamente quando si installa Office sul computer di sviluppo. Per altre informazioni, vedere [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Gli assembly di interoperabilità primari di Office non sono richiesti per l'esecuzione di soluzioni Office sui computer degli utenti finali. Per altre informazioni, vedere [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
##  <a name="usingfeatures"></a> Using Features of Multiple Microsoft Office Applications in a Single Project  
 Ogni modello di progetto di Office in Visual Studio è progettato per funzionare con una singola applicazione di Microsoft Office. Per usare le funzionalità in più applicazioni di Microsoft Office oppure per usare funzionalità in un'applicazione o un componente che non ha un progetto in Visual Studio, è necessario aggiungere un riferimento agli assembly di interoperabilità primari richiesti.  
  
 Nella maggior parte dei casi è necessario aggiungere riferimenti agli assembly di interoperabilità primari installati da Visual Studio nella directory %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools per Office\PIA\. Queste versioni degli assembly saranno visualizzate nella scheda **Framework** della finestra di dialogo **Gestione riferimenti** . Per altre informazioni, vedere [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
 Se sono stati installati e registrati gli assembly di interoperabilità primari nella Global Assembly Cache, queste versioni appariranno nella scheda **COM** della finestra di dialogo **Gestione riferimenti** . Evitare di aggiungere riferimenti a queste versioni degli assembly, perché possono verificarsi alcuni problemi di sviluppo durante il loro uso. Ad esempio, se sono state registrate versioni differenti degli assembly di interoperabilità primari nella Global Assembly Cache, il progetto verrà automaticamente associato all'ultima versione registrata dell'assembly, anche se è stata specificata una versione differente nella scheda **COM** della finestra di dialogo **Gestione riferimenti** .  
  
> [!NOTE]  
>  Alcuni assembly vengono aggiunti automaticamente a un progetto quando si aggiunge un assembly che vi fa riferimento. Ad esempio, i riferimenti agli assembly Office.dll e Microsoft.Vbe.Interop.dll verranno automaticamente aggiunti quando si aggiunge un riferimento agli assembly di Word, Excel, Outlook, Microsoft Forms o Graph.  
  
##  <a name="pialist"></a> Assembly di interoperabilità primari per applicazioni di Microsoft Office  
 Nella tabella seguente sono elencati gli assembly di interoperabilità primari disponibili per [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
|Applicazione o componente di Office|Nome dell'assembly di interoperabilità primario|  
|-------------------------------------|-----------------------------------|  
|Libreria oggetti di Microsoft Access 14.0<br /><br /> Libreria oggetti di Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Libreria oggetti del modulo di gestione di database di Access di Microsoft Office 14.0<br /><br /> Libreria oggetti del modulo di gestione di database di Access di Microsoft Office 15.0|Microsoft.Office.Interop.Access.Dao.dll|  
|Libreria oggetti di Microsoft Excel 14.0<br /><br /> Libreria oggetti di Microsoft Excel 15.0|Microsoft.Office.Interop.Excel.dll|  
|Libreria oggetti di Microsoft Graph 14.0 (usata da PowerPoint, Access e Word per i grafici)<br /><br /> Libreria oggetti di Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Libreria dei tipi Microsoft InfoPath 2.0 (solo per InfoPath 2007)|Microsoft.Office.Interop.InfoPath.dll|  
|Assembly di interoperabilità XML di Microsoft InfoPath (solo per InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Libreria oggetti Microsoft Office 14.0 (funzionalità condivisa di Office)<br /><br /> Libreria oggetti Microsoft Office 15.0 (funzionalità condivisa di Office)|office.dll|  
|Microsoft Office Outlook - Controllo visualizzazione (può essere usato in applicazioni e pagine Web per accedere alla cartella Posta in arrivo)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Libreria oggetti di Microsoft Outlook 14.0<br /><br /> Libreria oggetti di Microsoft Outlook 15.0|Microsoft.Office.Interop.Outlook.dll|  
|Libreria oggetti di Microsoft PowerPoint 14.0<br /><br /> Libreria oggetti di Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Libreria oggetti di Microsoft Project 14.0<br /><br /> Libreria oggetti di Microsoft Project 15.0|Microsoft.Office.Interop.MSProject.dll|  
|Libreria oggetti di Microsoft Publisher 14.0<br /><br /> Libreria oggetti di Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Libreria riferimenti a oggetti Web di Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Libreria riferimenti a oggetti pagina di Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Libreria dei tipi Microsoft Smart Tags 2.0 **Nota:** Smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Libreria dei tipi Microsoft Visio 14.0<br /><br /> Libreria dei tipi Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|  
|Libreria dei tipi Salva come pagina Web Microsoft Visio 14.0<br /><br /> Libreria dei tipi Salva come pagina Web Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Libreria dei tipi controlli disegno di Microsoft Visio 14.0<br /><br /> Libreria dei tipi controlli disegno di Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Libreria oggetti di Microsoft Word 14.0<br /><br /> Libreria oggetti di Microsoft Word 15.0|Microsoft.Office.Interop.Word.dll|  
|Microsoft Visual Basic, Applications Edition Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Assembly di reindirizzamento delle associazioni  
 Quando si installano e registrano gli assembly di interoperabilità primari di Office nella Global Assembly Cache (tramite Office o installando il pacchetto ridistribuibile per gli assembly di interoperabilità primari), gli assembly di reindirizzamento delle associazioni sono anche installati solo nella Global Assembly Cache. Questi assembly garantiscono che in fase di esecuzione venga caricata la versione corretta degli assembly di interoperabilità primari. Quando ad esempio una soluzione che fa riferimento a un assembly di interoperabilità primario di [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] viene eseguita in un computer in cui è installata la versione [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] dello stesso assembly, l'assembly di reindirizzamento delle associazioni indica al runtime di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i caricare la versione [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] dell'assembly di interoperabilità primario. Per altre informazioni, vedere [Procedura: abilitare e disabilitare il reindirizzamento di associazione automatico](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Panoramica del modello oggetto di Excel](../vsto/excel-object-model-overview.md)   
 [Soluzioni InfoPath](../vsto/infopath-solutions.md)   
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)   
 [Soluzioni Project](../vsto/project-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Riferimenti generali &#40; sviluppo per Office in Visual Studio &#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  