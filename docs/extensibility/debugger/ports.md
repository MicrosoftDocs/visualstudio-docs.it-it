---
title: Porte | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6378ddc2663e4ecf239c78ede96f0c1bc12d77a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ports"></a>Porte
In termini di architettura del debugger, un **porta**:  
  
-   È un contenitore per un set di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo basato su Windows CE tramite un cavo, o a una macchina di DCOM in rete. Una porta speciale, chiamata sulla porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
-   Grado di identificarsi per nome o identificatore.  
  
-   Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare i processi.  
  
-   È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce una porta predefinita che gestisce i processi basati su Windows, gestiti e nativi. Una porta personalizzata deve essere implementata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, un fornitore di porta personalizzato deve inoltre essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)