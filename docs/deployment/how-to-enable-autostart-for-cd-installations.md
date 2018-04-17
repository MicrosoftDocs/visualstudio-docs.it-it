---
title: "Procedura: attivare l'avvio automatico per installazioni da CD | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 896d0f97df444ae24e81037e49d211084e5f577e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Procedura: attivare l'avvio automatico per le installazioni da CD
Quando si distribuisce un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione tramite supporti rimovibili, ad esempio CD-ROM o DVD-ROM, è possibile abilitare `AutoStart` in modo che il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene avviata automaticamente dopo l'inserimento del supporto.  
  
 `AutoStart` può essere abilitata sul **pubblica** pagina del **creazione progetti**.  
  
### <a name="to-enable-autostart"></a>Per abilitare l'avvio automatico  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **opzioni** pulsante.  
  
     Il **opzioni di pubblicazione** viene visualizzata la finestra di dialogo.  
  
4.  Fare clic su **distribuzione**.  
  
5.  Selezionare il **per installazioni da CD, avvia automaticamente l'installazione all'inserimento del CD** casella di controllo.  
  
     Un file Autorun verrà copiato nel percorso di pubblicazione è pubblicata l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)