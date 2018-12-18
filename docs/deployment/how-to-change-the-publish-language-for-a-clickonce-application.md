---
title: 'Procedura: modificare la lingua di pubblicazione per un''applicazione ClickOnce | Documenti Microsoft'
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
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 7d368f036e8a5f8599a802bb6f57eba7bc6d767d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procedura: cambiare la lingua di pubblicazione di un'applicazione ClickOnce
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, l'interfaccia utente visualizzata durante l'installazione verrà impostata automaticamente la lingua del computer di sviluppo. Se si pubblica un'applicazione localizzata, è necessario specificare una lingua e delle impostazioni cultura in base alla versione localizzata. Ciò è dovuto il `Publish language` proprietà per il progetto.  
  
 Il `Publish language` proprietà può essere impostata **opzioni di pubblicazione** la finestra di dialogo, accessibile dal **pubblica** pagina del **progettazione**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-change-the-publish-language"></a>Per modificare la lingua di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **opzioni** pulsante per aprire la **opzioni di pubblicazione** la finestra di dialogo.  
  
4.  Fare clic su **descrizione**.  
  
5.  Nel **opzioni di pubblicazione** finestra di dialogo, selezionare una lingua e le impostazioni cultura dal **lingua di pubblicazione** elenco a discesa e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)