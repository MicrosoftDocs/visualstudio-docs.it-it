---
title: Limitazioni del debug di WCF | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14340ad3a19feb6340b836b1db8d71b3a8adcd83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="limitations-on-wcf-debugging"></a>Limitazioni del debug di WCF
Sono disponibili tre modalità per avviare il debug di un servizio WCF:  
  
-   Si esegue il debug di un processo client che chiama un servizio. Il debugger esegue le istruzioni del servizio. Il servizio non deve essere presente nella stessa soluzione dell'applicazione client.  
  
-   Si esegue il debug di un processo client che effettua una richiesta a un servizio. Il servizio deve essere parte della soluzione.  
  
-   Utilizzare **Connetti a processo** da collegare a un servizio che è attualmente in esecuzione. Il debug inizia all'interno del servizio.  
  
 In questo argomento vengono descritte le limitazioni di questi scenari.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitazioni dell'esecuzione di istruzioni in un servizio  
 Per eseguire istruzioni in un servizio da un'applicazione client di cui si esegue il debug, è necessario soddisfare le seguenti condizioni:  
  
-   Il client deve chiamare il servizio utilizzando un oggetto client sincrono.  
  
-   L'operazione del contratto non può essere unidirezionale.  
  
-   Se il server è asincrono, non è possibile visualizzare lo stack di chiamate completo durante l'esecuzione del codice nel servizio.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     È necessario aggiungere questo codice solo una volta. È possibile aggiungere questo codice modificando il file con estensione config o la connessione al servizio utilizzando **Connetti a processo**. Quando si utilizza **Connetti a processo** in un servizio, il codice di debug viene aggiunto automaticamente al file config. Successivamente, è possibile eseguire il debug e le istruzioni nel servizio senza dover modificare il file config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitazioni dell'uscita da un servizio  
 L'uscita da un servizio e il ritorno al client presenta le stesse limitazioni descritte per l'esecuzione delle istruzioni di un servizio. Inoltre, il debugger deve essere connesso al client. Se è in corso il debug di un client e l'esecuzione di istruzioni in un servizio, il debugger rimane connesso al servizio. È true se è stato avviato il client utilizzando **Avvia debug** o connesso al client tramite **Connetti a processo**. Se il debug è stato avviato mediante la connessione al servizio, il debugger non è ancora connesso al client. In tal caso, se è necessario uscire dal servizio e al client, è innanzitutto necessario utilizzare **Connetti a processo** connettersi manualmente al client.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitazioni della connessione automatica a un servizio  
 La connessione automatica a un servizio presenta le limitazioni riportate di seguito:  
  
-   Il servizio deve essere parte della soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di cui si esegue il debug.  
  
-   Il servizio deve essere ospitato. Può essere parte di un progetto di sito Web (File system e HTTP), un progetto di applicazione Web (File system e HTTP) o un progetto di libreria di servizi WCF. I progetti di libreria di servizi WCF possono essere librerie di servizi o librerie di servizi di flusso di lavoro.  
  
-   Il servizio deve essere richiamato da un client WCF.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Self-hosting  
 Oggetto *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, l'Host del servizio WCF, o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Server di sviluppo. Per informazioni su come eseguire il debug di un servizio indipendente, vedere [procedura: eseguire il Debug di un servizio WCF Self-Hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Self-hosting  
 Per abilitare il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazioni 3.0 o 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 deve essere installato prima [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] è installato. Se [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] viene installato prima [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, si verifica un errore quando si tenta di eseguire il debug di un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione 3.0 o 3.5. Il messaggio di errore è "Impossibile eseguire automaticamente l'istruzione sul server". Per risolvere questo problema, utilizzare le finestre **Pannello di controllo** > **programmi e funzionalità** per ripristinare il [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Procedura: Eseguire il debug di un servizio WCF indipendente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)