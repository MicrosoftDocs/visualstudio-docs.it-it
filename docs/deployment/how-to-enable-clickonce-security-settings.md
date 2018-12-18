---
title: 'Procedura: abilitare le impostazioni di sicurezza ClickOnce | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc3f87e590c6b915d5b3d9db5d2517d80965dd6c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procedura: abilitare le impostazioni di sicurezza ClickOnce
Sicurezza dall'accesso di codice per le applicazioni ClickOnce deve essere abilitato per pubblicare l'applicazione. Questa operazione viene eseguita automaticamente quando si pubblica un'applicazione mediante la pubblicazione guidata.  
  
 In alcuni casi, l'abilitazione di sicurezza dall'accesso di codice può influire sulle prestazioni durante la compilazione o il debug dell'applicazione. In questi casi, si desidera disabilitare temporaneamente le impostazioni di sicurezza.  
  
 Impostazioni di sicurezza ClickOnce possono essere abilitate o disabilitate sul **sicurezza** pagina del **progettazione**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Per abilitare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza** .  
  
3.  Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .  
  
     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella pagina protezione.  
  
    > [!NOTE]
    >  Questa casella di controllo è selezionata automaticamente ogni volta che l'applicazione viene pubblicata con di **pubblica** procedura guidata.  
  
### <a name="to-disable-clickonce-security-settings"></a>Per disabilitare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza** .  
  
3.  Cancella il **Abilita impostazioni di sicurezza ClickOnce** casella di controllo.  
  
     L'applicazione verrà eseguita con le impostazioni di sicurezza con attendibilità totale; le impostazioni per il **sicurezza** pagina verrà ignorata.  
  
    > [!NOTE]
    >  Ogni volta che l'applicazione viene pubblicata utilizzando la pubblicazione guidata, verrà selezionata la casella di controllo; è necessario cancellarlo nuovo termine di ogni pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
