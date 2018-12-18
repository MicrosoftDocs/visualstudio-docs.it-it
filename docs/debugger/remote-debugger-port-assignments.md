---
title: Le assegnazioni di porta del Debugger remoto | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c541922ac18c28e085db37b6ac9fa9349adbeb9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="remote-debugger-port-assignments"></a>Assegnazioni delle porte del debugger remoto
Visual Studio Remote Debugger può essere eseguito come applicazione o come servizio in background. Quando viene eseguito come applicazione, usa una porta assegnata per impostazione predefinita, come indicato di seguito:  

-   Visual Studio 2017:4022

-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 In altre parole, il numero della porta assegnata al debugger remoto viene incrementato di 2 per ogni versione. È possibile impostare un numero di porta diverso. In una sezione successiva verrà illustrato come impostare i numeri di porta.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 32 bit  
 TCP 4022 (in Visual Studio 2017) è la porta principale ed è obbligatorio per tutti gli scenari. Può essere configurata dalla riga di comando o nella finestra del debugger remoto.  
  
 Nella finestra del debugger remoto, fare clic su **strumenti > Opzioni**e impostare il numero di porta TCP/IP.  
  
 Nella riga di comando, avviare il debugger remoto con il **porta di inserimento/** passare: **msvsmon /port \<il numero di porta >**.  
  
 È possibile trovare tutti il debugger remoto opzioni della riga di comando nella Guida al debug remoto (premere **F1** oppure fare clic su **Guida > utilizzo** nella finestra del debugger remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 64 bit  
 Quando viene avviata la versione a 64 bit del debugger remoto, per impostazione predefinita Usa la porta 4022.  Se si esegue il debug di un processo a 32 bit, la versione a 64 bit del debugger remoto avvia una versione a 32 bit del debugger remoto sulla porta 4023. Se si esegue il debugger remoto a 32 bit, Usa 4022 e 4023 non viene utilizzato.  
  
 Questa porta è configurabile dalla riga di comando: **Msvsmon /wow64port \<il numero di porta >**.  
  
## <a name="the-discovery-port"></a>Porta di individuazione  
 La porta UDP 3702 viene usata per individuare le istanze in esecuzione del debugger remoto sulla rete, ad esempio la finestra di dialogo **Trova** nella finestra di dialogo **Connetti a processo** . Viene usata solo per l'individuazione di un computer che esegue il debugger remoto, pertanto è facoltativa se si ha altro un modo per conoscere il nome del computer o l'indirizzo IP del computer di destinazione. Si tratta di una porta standard per l'individuazione, quindi non è possibile configurare il numero di porta.  
  
 Se non si vuole attivare l'individuazione, è possibile avviare msvsmon dalla riga di comando con l'individuazione disabilitata:  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Porte del debugger remoto in Azure  
 Il debugger remoto in Azure usa le porte indicate di seguito. Le porte del servizio cloud sono mappate alle porte nelle singole macchine virtuali. Tutte le porte sono TCP.  
  
||||  
|-|-|-|  
|**Connessione**|**Porta sul servizio cloud**|**Porta sulla macchina virtuale**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)