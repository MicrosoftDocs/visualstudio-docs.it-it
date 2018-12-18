---
title: 'Procedura: eseguire il Debug di un servizio WCF Self-Hosted | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19ce90effca21f6079cc7b569fa6e58f94553627
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Procedura: eseguire il debug di un servizio WCF indipendente
Oggetto *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, l'Host del servizio WCF, o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Server di sviluppo. Il modo più semplice per eseguire il debug di un servizio WCF indipendente consiste nel configurare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare i client e server quando si sceglie **Avvia debug** sul **Debug** menu.  
  
 Se il servizio WCF è indipendente all'interno o un processo che non può essere avviato in questo modo, ad esempio il servizio NT, è possibile utilizzare questo metodo. È possibile invece effettuare una delle seguenti:  
  
-   Connettere manualmente il debugger al processo di hosting. Per ulteriori informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     oppure  
  
-   Avviare il debug di client e quindi eseguire una chiamata al servizio. Questo richiede l'abilitazione del debug nel file app. config. Per ulteriori informazioni, [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Per avviare i client e host da Visual Studio  
  
1.  Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione contenente progetti client e server.  
  
2.  Configurare la soluzione per avviare i processi client e server quando si sceglie **avviare** sul **Debug** menu.  
  
    1.  In **Esplora**, fare doppio clic sul nome della soluzione.  
  
    2.  Fare clic su **Imposta progetti di avvio**.  
  
    3.  Nel **soluzione \<nome > proprietà** nella finestra di dialogo **più progetti di avvio**.  
  
    4.  Nel **più progetti di avvio** griglia, nella riga che corrisponde al progetto server, fare clic su **azione** e scegliere **avviare**.  
  
    5.  Fare clic sulla riga che corrisponde al progetto client, **azione** e scegliere **avviare**.  
  
    6.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Procedura: Eseguire istruzioni nei servizi WCF](../debugger/how-to-step-into-wcf-services.md)