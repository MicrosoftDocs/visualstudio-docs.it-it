---
title: 'Procedura: pubblicare versione automaticamente incremento ClickOnce | Documenti Microsoft'
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
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 2e1399795400d52543b92cb13635a8485b160f22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedura: incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce
Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, la modifica di `Publish Version` fa sì che l'applicazione viene pubblicata come aggiornamento. Per impostazione predefinita, viene incrementato automaticamente il `Revision` numero il `Publish Version` ogni volta che si pubblica l'applicazione.  
  
 È possibile disabilitare questo comportamento nel **pubblica** pagina del **progettazione**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Per disabilitare l'incremento automatico della versione di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Nel **versione pubblicazione** sezione, deselezionare il **incrementa automaticamente revisione a ogni versione** casella di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)