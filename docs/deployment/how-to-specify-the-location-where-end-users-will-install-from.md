---
title: 'Procedura: specificare il percorso in cui gli utenti finali eseguiranno l''installazione da | Documenti Microsoft'
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
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a3a2770933f4a9f600b12a2d601deca855de3a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Procedura: specificare il percorso da cui gli utenti finali eseguiranno l'installazione
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, il percorso in cui gli utenti accedere per scaricare e installare l'applicazione non è necessariamente il percorso in cui è inizialmente a pubblicare l'applicazione. Ad esempio, in alcune organizzazioni uno sviluppatore può pubblicare un'applicazione a un server di gestione temporanea e quindi un amministratore sposterebbe l'applicazione a un server Web.  
  
 In questo caso, è possibile utilizzare il `Installation URL` proprietà per specificare il server Web in cui accederanno gli utenti di scaricare l'applicazione. Ciò è necessario in modo che il manifesto dell'applicazione in grado di cercare gli aggiornamenti.  
  
 Il `Installation URL` proprietà può essere impostata sul **pubblica** pagina del **progettazione**.  
  
 **Nota** il `Installation URL` proprietà può essere impostata anche utilizzando la **PublishWizard**. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Per specificare un URL di installazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Nel campo URL di installazione, immettere il percorso di installazione utilizzando un URL completo, utilizzando il formato http://www.microsoft.com/ApplicationName o un percorso UNC nel formato \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)