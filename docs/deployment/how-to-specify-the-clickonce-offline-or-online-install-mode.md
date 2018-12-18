---
title: "Procedura: specificare il Offline di ClickOnce o installare la modalità Online | Documenti Microsoft"
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b1c0f8615513639081351bdf77ea9ec63fc8309b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procedura: specificare la modalità di installazione online o offline di ClickOnce
Il `Install Mode` per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione determina se l'applicazione sarà disponibile online o offline. Quando si sceglie **l'applicazione è disponibile solo online**, l'utente deve disporre di accesso per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] percorso di pubblicazione (pagina Web o una condivisione file) per eseguire l'applicazione. Quando si sceglie **l'applicazione è disponibile offline nonché**, l'applicazione aggiunge voci per il **avviare** menu e **Aggiungi / Rimuovi programmi** la finestra di dialogo; l'utente è in grado di eseguire l'applicazione quando non sono connessi.  
  
 Il `Install Mode` può essere impostata sul **pubblica** pagina del **progettazione**.  
  
 **Nota** il `Install Mode` può essere impostato anche utilizzando la pubblicazione guidata. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Per rendere un'applicazione ClickOnce disponibile solo online  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Nel **modalità di installazione e le impostazioni** area, fare clic su di **l'applicazione è disponibile solo online** pulsante di opzione.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Per rendere disponibile un'applicazione ClickOnce online o offline  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Nel **modalità di installazione e le impostazioni** area, fare clic su di **l'applicazione è disponibile offline nonché** pulsante di opzione.  
  
     Durante l'installazione, l'applicazione aggiunge voci per il **avviare** menu e a **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)