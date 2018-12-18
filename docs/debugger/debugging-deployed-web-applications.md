---
title: Debug di applicazioni ASP.NET distribuito | Documenti Microsoft
ms.custom: 
ms.date: 06/30/2017
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
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 072c5cde6a4a0af81397863db36bbf861b7ef0ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-deployed-aspnet-applications"></a>Debug di applicazioni ASP.NET distribuito
Per utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire il debug di un'applicazione distribuita, è necessario effettuare la connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificare che il debugger abbia accesso ai simboli per l'applicazione. Inoltre, è necessario individuare e aprire i file di origine dell'applicazione. Per ulteriori informazioni, vedere [specificare simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), e [requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> Se si collega al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo di lavoro per il debug e raggiunto un punto di interruzione, tutto il codice gestito nel processo di lavoro verrà interrotto. L'arresto di tutto il codice gestito nel processo di lavoro può comportare l'arresto del lavoro per tutti gli utenti del server. Prima di eseguire il debug su un server di produzione, tenere in considerazione il potenziale impatto sulle attività produttive. 
  
La connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è praticamente identica alla connessione a qualsiasi altro processo remoto. Quando si è connessi, se non è aperto il progetto corretto, viene visualizzata una finestra di dialogo quando l'applicazione si interrompe. In questa finestra di dialogo è necessario immettere il percorso dei file di origine dell'applicazione. Il nome file specificato nella finestra di dialogo deve corrispondere a quello specificato nei simboli di debug, che si trovano sul server Web. Per ulteriori informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Per impostare il debug remoto in IIS, vedere [ASP.NET di debug remoto in un Computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  Molte applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fanno riferimento a DLL contenenti logica di business o altro codice utile. Quando si distribuisce l'app, tale riferimento copia la DLL dal computer locale alla cartella \bin della directory virtuale dell'applicazione Web. Quando si esegue il debug, tenere presente che l'applicazione Web fa riferimento a tale copia della DLL e non alla copia presente sul computer locale. 
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Procedura: abilitare il debug per le applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)