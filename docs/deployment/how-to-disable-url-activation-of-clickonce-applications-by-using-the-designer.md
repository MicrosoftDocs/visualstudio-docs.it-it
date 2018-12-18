---
title: "Procedura: disabilitare l'attivazione dell'URL di applicazioni ClickOnce tramite la finestra di progettazione | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 366c4362ca3c3b6140380ab64000a01fe8e1aa6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
In genere, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione verrà avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile scegliere di disabilitare questo comportamento e indicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. E non può essere utilizzato per le applicazioni solo online, che possono essere avviate solo utilizzando l'URL. Per ulteriori informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura utilizza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È inoltre possibile eseguire questa attività utilizzando la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Per ulteriori informazioni, vedere [procedura: disabilitare l'attivazione URL di applicazioni di ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Fare doppio clic sul nome del progetto in **Esplora**, fare clic su **proprietà**.  
  
2.  Nel **proprietà** pagina, fare clic su di **pubblica** scheda.  
  
3.  Fare clic su **Opzioni**.  
  
4.  Fare clic su **manifesti**.  
  
5.  Selezionare la casella di controllo **blocco attivazione tramite un URL dell'applicazione**.  
  
6.  Distribuire l'applicazione,  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)