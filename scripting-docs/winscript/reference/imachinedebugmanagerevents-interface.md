---
title: Interfaccia IMachineDebugManagerEvents | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfaccia IMachineDebugManagerEvents
Segnala le modifiche nell'esecuzione elenco applicazione gestito dal gestore di debug macchina. Questa interfaccia può essere utilizzata dal debugger IDE per visualizzare un elenco dinamico di applicazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IMachineDebugManagerEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gestisce l'evento quando un'applicazione viene aggiunto all'esecuzione elenco di applicazioni.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gestisce l'evento quando un'applicazione viene rimossa l'esecuzione di elenco di applicazioni.|