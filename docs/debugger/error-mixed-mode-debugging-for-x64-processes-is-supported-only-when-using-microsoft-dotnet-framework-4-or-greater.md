---
title: "Errore: In modalità mista debug per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 87ca4ffe1a80d6d6fdc948c3a1617f888aba4baf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 4. Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] precedenti alla 4 non è supportato.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Effettuare uno dei passaggi indicati di seguito.  
  
    -   Aggiornare [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] alla versione 4.  
  
    -   Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)