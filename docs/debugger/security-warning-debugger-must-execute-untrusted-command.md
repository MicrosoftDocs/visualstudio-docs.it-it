---
title: 'Avviso di sicurezza: Il Debugger deve eseguire un comando non attendibile | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8749cea92e0ee16a14ecbaa3cc8732131c5a7f51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avviso di sicurezza: il debugger deve eseguire un comando non attendibile
Questa finestra di dialogo di avviso viene visualizzata quando si usa il server di origine. Indica che il comando che deve essere eseguito dal debugger per ottenere il codice sorgente non è incluso nell'elenco dei comandi attendibili per il server di origine contenuto nel file srcsvr.ini. Se il comando è valido, è possibile aggiungerlo al file srcsvr.ini. In caso contrario, è opportuno non eseguirlo. Per altre informazioni, vedere [Specifica di file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Testo del messaggio  
 **Il debugger deve eseguire il seguente comando non attendibile per ottenere il codice sorgente dal server di origine.**  
  
 **Se il debug dei file di simboli (\*con estensione pdb) è non da un'origine conosciuta e attendibile, questo comando potrebbe essere non valido o pericoloso da eseguire.**  
  
 **Si desidera eseguire questo comando?**  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Casella di testo  
 Comando del file con estensione pdb da eseguire.  
  
 Run  
 Consente l'esecuzione del comando.  
  
 Non eseguire  
 Arresta l'esecuzione del comando e il download del file dal server di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)