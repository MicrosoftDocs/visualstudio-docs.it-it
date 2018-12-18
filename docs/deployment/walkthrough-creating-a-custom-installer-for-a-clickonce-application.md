---
title: 'Procedura dettagliata: Creazione di un programma di installazione personalizzato per un''applicazione ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 06c048db48173913a2e1102d1e70f07369316439
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce
Qualsiasi applicazione ClickOnce in base a un file .exe può essere installati automaticamente e aggiornata dal programma di installazione personalizzato. Un programma di installazione personalizzato può implementare un'esperienza utente migliorata durante l'installazione, tra cui le finestre di dialogo personalizzate per le operazioni di manutenzione e di sicurezza. Per eseguire operazioni di installazione, il programma di installazione personalizzato utilizza il <xref:System.Deployment.Application.InPlaceHostingManager> classe. Questa procedura dettagliata viene illustrato come creare un programma di installazione personalizzato per l'installazione invisibile all'utente di un'applicazione ClickOnce.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Per creare un programma di installazione di applicazioni ClickOnce personalizzato  
  
1.  In un'applicazione ClickOnce, aggiungere riferimenti a System. Deployment e Forms.  
  
2.  Aggiungere una nuova classe all'applicazione e specificare qualsiasi nome. Questa procedura dettagliata viene utilizzato il nome `MyInstaller`.  
  
3.  Aggiungere il seguente `Imports` o `using` istruzioni all'inizio della nuova classe.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Aggiungere i metodi seguenti alla classe.  
  
     Chiamano questi metodi <xref:System.Deployment.Application.InPlaceHostingManager> metodi per scaricare il manifesto di distribuzione, l'asserzione delle autorizzazioni appropriate, chiedere all'utente l'autorizzazione per l'installazione e quindi scaricare e installare l'applicazione nella cache di ClickOnce. Un programma di installazione personalizzato è possibile specificare che un'applicazione ClickOnce è pre-attendibile, o è possibile posticipare la decisione sull'attendibilità di <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chiamata al metodo. Questo codice pre-attendibile l'applicazione.  
  
    > [!NOTE]
    >  Le autorizzazioni assegnate concedendo pre-l'attendibilità di non possono superare le autorizzazioni del codice programma di installazione personalizzato.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Per eseguire l'installazione dal codice, chiamare il `InstallApplication` metodo. Ad esempio, se la classe è denominata `MyInstaller`, è possibile chiamare `InstallApplication` nel modo seguente.  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>Passaggi successivi  
 Un'applicazione ClickOnce è anche possibile aggiungere logica di aggiornamento personalizzata, tra cui un'interfaccia utente personalizzata per mostrare durante il processo di aggiornamento. Per altre informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>. Un'applicazione ClickOnce può inoltre eliminare la voce di menu Start standard, collegamento e voce Aggiungi / Rimuovi programmi mediante un `<customUX>` elemento. Per ulteriori informazioni, vedere [ \<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md)