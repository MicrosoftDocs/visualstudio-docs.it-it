---
title: Problemi di sicurezza | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d45ebd8c4d80b84749838c2034d72159c9e39627
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="security-issues"></a>Problemi relativi alla sicurezza
Per eseguire il debug di un programma in Visual Studio, solo le autorizzazioni necessite sono gli stessi necessari per eseguire il programma. Ciò include il debug remoto per la maggior parte delle situazioni (alcune situazioni che coinvolgono altri servizi, ad esempio Internet Information Service, potrebbe essere necessario un livello superiore di autorizzazioni).  
  
 Durante l'esecuzione di Visual Studio, il gestore di debug di processi (PDM) tiene traccia dei processi di debug nel computer locale. In modalità remota, un programma denominato msvsmon.exe viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibili PDM. Si noti che msvsmon.exe non è un servizio e deve essere avviato manualmente per abilitare il debug remoto nel computer. Quando Visual Studio (o msvsmon.exe) non è in esecuzione, nessun processo viene tenuta traccia per il debug.  
  
 Ciò significa che uno sviluppatore possibile eseguire il debug di programmi che egli avviato senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug di processi avviati da un altro utente, se tale persona è un membro dello stesso gruppo di sicurezza. E per abilitare il debug remoto, è necessario solo per copiare i necessari file all'istanza remota del computer e avviare msvsmon.exe (vedere [il debug remoto](../../debugger/remote-debugging.md) per altri dettagli).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Gestione di Debug di processi](../../extensibility/debugger/process-debug-manager.md)   
 [Debug remoto](../../debugger/remote-debugging.md)