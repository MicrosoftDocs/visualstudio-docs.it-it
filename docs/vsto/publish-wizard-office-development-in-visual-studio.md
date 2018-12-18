---
title: Pubblicazione guidata (sviluppo per Office in Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67e3222c6f1deeca58b84aca4ba73d2826483b26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Pubblicazione guidata (sviluppo per Office in Visual Studio)
  Utilizzare il **pubblicazione guidata** per copiare i file di soluzione in una posizione specifica, creare i file manifesto e creare un programma di installazione.  
  
 Per accedere a questa procedura guidata, scegliere il **compilare** menu, scegliere **pubblica** *SolutionName*. È inoltre possibile accedere il **pubblicazione guidata** da **Esplora**. Aprire il menu di scelta rapida per il nodo del progetto e quindi scegliere **pubblica**.  
  
 Ogni sezione riportata di seguito descrive una pagina della procedura guidata.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>In cui si desidera pubblicare l'applicazione?  
 **Specificare il percorso in cui pubblicare l'applicazione**  
 Obbligatorio. Percorso di pubblicazione è la directory in cui il **pubblicazione guidata** copia i file della soluzione, ad esempio i manifesti, gli assembly, il certificato temporaneo e altri file della compilazione. È necessario l'accesso in scrittura a questa directory.  
  
 Digitare il percorso come un percorso su disco, una condivisione file, un sito FTP o URL del sito web oppure fare clic su di **Sfoglia** per cercare il percorso. Il percorso può essere nei seguenti formati:  
  
-   Un percorso relativo o assoluto in formato standard di Windows, ad esempio C:\Deploy\MyApplication o \MyApplication.  
  
-   Un percorso UNC Universal Naming Convention (), ad esempio \\\ServerName\MyApplication\\.  
  
-   Un URL di un sito web del sito, ad esempio http://www.microsoft.com/MyApplication.  
  
 Per impostazione predefinita, il percorso di pubblicazione viene *http://localhost/projectname/* se IIS è installato o la directory Publish \ se si è installato IIS.  
  
> [!NOTE]  
>  Se il computer di destinazione è in esecuzione Windows Vista, esistono altre considerazioni. È necessario essere un amministratore nel computer Windows Vista, utilizzare l'opzione di pubblicazione locale. Inoltre, il percorso predefinito è sempre il *pubblicare\\*  directory, indipendentemente dal fatto che IIS sia installato.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Che cos'è il percorso di installazione predefinito nei computer degli utenti finali?  
 Il percorso di installazione è facoltativo. Se si preferisce, è possibile impostare il percorso di installazione in un secondo momento. Per informazioni dettagliate, vedere [procedura: modificare il percorso di installazione di una soluzione Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Il percorso di installazione è la directory da cui l'utente finale installa la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. Il **pubblicazione guidata** distribuisce la soluzione a questo percorso, a meno che il percorso corrisponde a quello immesso nella **specificare il percorso in cui pubblicare l'applicazione** casella nella pagina precedente.  
  
 **Da un sito Web**  
 Specificare l'URL che gli utenti finali utilizzeranno per installare la soluzione.  
  
 **Da una condivisione di file o il percorso UNC**  
 Specificare il percorso UNC che gli utenti finali utilizzeranno per installare la soluzione.  
  
 **Da un CD-ROM o DVD-ROM**  
 Questa opzione non richiede un percorso di installazione.  
  
 Visual Studio masterizzare il CD o DVD. È necessario copiare manualmente l'output a un CD o DVD.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Pagina pubblica, Progettazione progetti &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  