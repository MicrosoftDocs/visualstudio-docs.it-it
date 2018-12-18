---
title: 'Procedura: specificare una pagina di pubblicazione per un''applicazione ClickOnce | Documenti Microsoft'
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 491ef29c955c5ab06b8539ec5089f2ed32feaf36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione, una pagina Web predefinita (publish.htm) viene generata e pubblicata insieme all'applicazione. Questa pagina contiene il nome dell'applicazione, un collegamento per installare l'applicazione e/o tutti i prerequisiti e un collegamento a un argomento della Guida che descrivono [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il **pubblica pagina** proprietà per il progetto consente di specificare un nome per la pagina Web per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
 Dopo la pagina di pubblicazione è stata specificata, la volta successiva che si pubblica, viene copiato nel percorso di pubblicazione; non verrà sovrascritto se si pubblica nuovamente. Se si desidera personalizzare l'aspetto della pagina, è possibile farlo senza preoccuparsi di perdere le modifiche. Per ulteriori informazioni, vedere [procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Il **pubblica pagina** proprietà può essere impostata **opzioni di pubblicazione** la finestra di dialogo, accessibile dal **pubblica** riquadro del **progettazione**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Per specificare una pagina Web personalizzata per un'applicazione ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il **pubblica** riquadro.  
  
3.  Fare clic su di **opzioni** pulsante per aprire la **opzioni di pubblicazione** la finestra di dialogo.  
  
4.  Fare clic su **distribuzione**.  
  
5.  Nel **opzioni di pubblicazione** finestra di dialogo, assicurarsi che il **pagina web di distribuzione aperti dopo la pubblicazione** casella di controllo è selezionata (deve essere selezionato per impostazione predefinita).  
  
6.  Nel **pagina web di distribuzione:** casella, immettere il nome della pagina Web e quindi fare clic su **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Per impedire l'avvio di ogni volta che pubblica la pagina di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il **pubblica** riquadro.  
  
3.  Fare clic su di **opzioni** pulsante per aprire la **opzioni di pubblicazione** la finestra di dialogo.  
  
4.  Fare clic su **distribuzione**.  
  
5.  Nel **opzioni di pubblicazione** la finestra di dialogo, deseleziona il **pagina web di distribuzione aperti dopo la pubblicazione** casella di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)