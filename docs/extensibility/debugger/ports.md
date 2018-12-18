---
title: Porte | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a350e0579f7e60d8a7ffc3e879d79364cfdf0317
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ports"></a>Porte
In termini di architettura del debugger, un **porta**:  
  
-   È un contenitore per un set di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo basato su Windows CE tramite un cavo, o a una macchina di DCOM in rete. Una porta speciale, chiamata sulla porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
-   Grado di identificarsi per nome o identificatore.  
  
-   Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare i processi.  
  
-   È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, gestiti e nativi. Una porta personalizzata deve essere implementata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, un fornitore di porta personalizzato deve inoltre essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)