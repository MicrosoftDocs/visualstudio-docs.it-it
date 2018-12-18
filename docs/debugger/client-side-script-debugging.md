---
title: Il debug degli Script lato client | Documenti Microsoft
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f31897cc4fb48fd7c814d4d25cb41ce0cb7e57da
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="client-side-script-debugging"></a>Debug di script sul lato client
Il debugger di Visual Studio offre un ambiente di debug completo per l'individuazione e la correzione degli errori negli script lato client delle pagine ASP.NET.  
  
## <a name="opening-script-documents"></a>Apertura di documenti di script  
È possibile visualizzare gli elenchi di documenti di script sul lato server e lato client nel **Esplora** da visualizzare. È possibile aprire qualsiasi documento di script da **Esplora soluzioni**. Per altre informazioni, vedere [How to: View Script Documents](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapping dei punti di interruzione  
 In Visual Studio non è possibile eseguire direttamente il debug di codice lato server, ma è possibile impostare un punto di interruzione in un file lato server. Visual Studio esegue automaticamente il mapping del punto di interruzione a un percorso corrispondente del file lato client e crea un punto di interruzione associato nel codice lato client.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Connessione manuale o automatica a script  
 Per avviare il debug di script in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il debugger deve essere connesso allo script del quale si desidera eseguire il debug. Questa operazione può essere eseguita manualmente o automaticamente.  
  
 È possibile eseguire la connessione manualmente utilizzando l'interfaccia del debugger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per scegliere il processo di script in esecuzione desiderato. Per altre informazioni, vedere [How to: Attach to Script](../debugger/how-to-attach-to-script.md).  
  
 Il debugger si connette automaticamente allo script quando si verifica uno dei seguenti casi:  
  
-   Rilevamento di punti di interruzione impostati nello script.  
  
-   Rilevamento di un'istruzione `Stop` VBScript o un'istruzione `debugger` JScript nel codice script.  
  
-   Rilevamento di un errore di sintassi o di runtime nello script da parte del browser o del server. In tal caso, verrà visualizzata una finestra di dialogo con l'opzione per iniziare il debug.  
  
 In caso di connessione manuale allo script, l'esecuzione del processo di script continua fino a quando viene nuovamente arrestato. È possibile arrestarlo scegliendo **Interrompi** dal menu **Debug** .  
  
 Quando il debugger viene connesso automaticamente, l'esecuzione degli script viene arrestata nella riga dove si rileva il punto di interruzione, l'istruzione `Stop` o l'istruzione `debugger` o un errore, o nel punto scelto per iniziare il debug in Internet Explorer.  
  
 A tal punto, è possibile utilizzare le comuni utilità del debugger per iniziare il debug. Ad esempio, è possibile utilizzare i comandi **Esegui** per continuare a eseguire il codice riga per riga. Per visualizzare e controllare il flusso di script è possibile utilizzare la finestra **Stack di chiamate** . Per visualizzare o modificare le variabili e le proprietà utilizzare le finestre delle variabili o la finestra di **controllo immediato** .  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Messaggi di errore avanzati per il debug di script  
 Visual Studio offre messaggi di errore avanzati per problemi di debug di script comuni. Questi messaggi vengono visualizzati solo in caso di connessione manuale a Internet Explorer. Se si verifica una condizione di errore all'apertura automatica di Internet Explorer, provare la connessione manuale in modo da poter vedere i messaggi di errore.  
  
## <a name="debugging-ajax-script-applications"></a>Debug di applicazioni script AJAX  
 Nelle applicazioni Web che supportano AJAX viene fatto largo uso di codice script e vengono poste serie problematiche di debug. Per informazioni sulle tecniche di debug AJAX, vedere  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitazioni del debug di Script](../debugger/limitations-on-script-debugging.md)   
 [Finestre delle variabili](../debugger/debugger-windows.md)   
 [Finestra di controllo immediato](../ide/reference/immediate-window.md)   
 [Debug e traccia panoramica delle applicazioni Ajax](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
