---
title: 'Procedura: rispondere per il debug Just-In-Time | Documenti Microsoft'
ms.custom: 
ms.date: 05/23/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c954cd95da7b6dd2ba0c2938852b939ae396525
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Procedura: rispondere per il debug Just-In-Time

Le azioni necessarie quando viene visualizzato Just-in-Time nella finestra di dialogo debugger variano a seconda che si sta tentando di effettuare:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Se si desidera risolvere o eseguire il debug dell'errore (gli utenti di Visual Studio)

- È necessario disporre di [installato Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48146) per visualizzare le informazioni dettagliate sull'errore e provare a eseguire il debug. Per ulteriori informazioni, vedere [eseguire il Debug utilizzando il Debugger JIT](../debugger/debug-using-the-just-in-time-debugger.md). Se non è possibile risolvere l'errore e correggere l'app, contattare il proprietario dell'app per risolvere l'errore.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Se si desidera impedire la visualizzazione nella finestra di dialogo Debugger JIT

È possibile eseguire i passaggi per impedire Just-in-Time la finestra di dialogo Debugger venga visualizzato. Se l'applicazione gestisce l'errore, è possibile eseguire l'applicazione normalmente.

1. (App web) Se si sta tentando di eseguire un'applicazione web, è possibile disabilitare il debug degli script.

    Per Internet Explorer o Edge, disabilitare il debug degli script nella finestra di dialogo Opzioni Internet. È possibile accedere a queste impostazioni dal **Pannello di controllo** > **rete e Internet** > **Opzioni Internet** (passaggi esatti dipendono le versione di Windows e il browser).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Riaprire la pagina web in cui è possibile trovare l'errore. Se si modifica questa impostazione non risolve il problema, contattare il proprietario dell'app web per risolvere il problema.

3. (Gli utenti di visual Studio) Se si è installato Visual Studio (o se è stato installato in precedenza e rimosso), [Just-in-Time di disabilitare il debug](../debugger/debug-using-the-just-in-time-debugger.md) e provare a eseguire nuovamente l'app.

    > [!IMPORTANT]
    > Se si disabilita Just-in-Time di debug e l'applicazione rileva un'eccezione non gestita (errore), verrà visualizzato una finestra di dialogo di errore standard invece o l'app verrà arrestato in modo anomalo o un blocco. L'app non verrà eseguita in genere finché non viene risolto l'errore (per utente o il proprietario dell'app).

2. (ASP.NET e IIS) Se si ospita un'applicazione Web ASP.NET in IIS, disabilitare il debug sul lato server.

    In Gestione IIS, fare doppio clic sul nodo del server e scegliere **passa a visualizzazione funzionalità**. Nella sezione ASP.NET scegliere **compilazione .NET** e assicurarsi di scegliere **False** come il comportamento di Debug (i passaggi sono diversi nelle versioni precedenti di IIS).
  
## <a name="see-also"></a>Vedere anche    
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)   
