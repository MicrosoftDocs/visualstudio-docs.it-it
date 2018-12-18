---
title: 'Procedura: versione di pubblicazione ClickOnce Set | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96bb991efed7d5a353fc7b73bcb647190438ff84
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: impostare la versione pubblicazione per un'applicazione ClickOnce
Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata un aggiornamento. Viene incrementato ogni versione della fase, l'applicazione verrà pubblicata come aggiornamento.  
  
 Il `Publish Version` proprietà può essere impostata sul **pubblica** pagina del **progettazione**.  
  
> [!NOTE]
>  È disponibile un'opzione di progetto che consente di incrementare automaticamente il `Publish Version` proprietà ogni volta che l'applicazione viene pubblicata; questa opzione è abilitata per impostazione predefinita. Per ulteriori informazioni, vedere [procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  In **versione pubblicazione** campo, incrementare la **principali**, **secondaria**, **compilare**, o **revisione** versione numeri.  
  
    > [!NOTE]
    >  È non necessario diminuire mai un numero di versione; In questo modo è possibile che il comportamento di aggiornamento imprevedibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)