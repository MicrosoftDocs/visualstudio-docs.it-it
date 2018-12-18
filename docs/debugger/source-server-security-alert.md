---
title: Avviso di sicurezza di Server di origine | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbb2233ffcc041a9d756ff51ac9fd3f1b9dc669e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="source-server-security-alert"></a>Avviso di sicurezza del server di origine
Quando viene utilizzato il server di origine, utilizzare unicamente file di simboli provenienti da un percorso conosciuto o attendibile.  
  
 Questo avviso viene visualizzato quando si attiva il supporto del server di origine. Comandi del Server di origine sono incorporati nei file di simboli di debug (***PDB** file). Assicurarsi di verificare l'origine dei file PDB.  
  
> [!IMPORTANT]
>  Quando viene utilizzato il server di origine, è necessario considerare i potenziali pericoli per la sicurezza indicati di seguito. Nel file pdb dell'applicazione possono essere incorporati comandi arbitrari, pertanto assicurarsi di inserire solo i comandi da eseguire nel file srcsrv.ini. Eventuali tentativi di eseguire un comando non presente nel file srcsvr.ini causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Poiché non viene eseguita alcuna convalida sui parametri dei comandi, prestare attenzione nell'utilizzare i comandi attendibili. Se ad esempio si considera attendibile il file cmd.exe, un utente malintenzionato potrebbe specificare parametri in grado di rendere dannoso il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
