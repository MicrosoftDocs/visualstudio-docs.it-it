---
title: Interfaccia IDebugThreadCall | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>Interfaccia IDebugThreadCall
Il `IDebugThreadCall` viene in genere implementata da un componente che effettua chiamate cross-thread con il `IDebugThread` il marshalling di implementazione fornita dal gestore di debug del processo (PDM).  
  
 Le chiamate PDM il `IDebugThreadCall` interfaccia nel thread desiderato e `IDebugThreadCall` interfaccia invia la chiamata all'implementazione desiderato. Il `IDebugThreadCall` le informazioni sui parametri passati nei parametri all'inizio appropriato esegue il cast di interfaccia.  
  
 Il `IDebugThreadCall` interfaccia è un oggetto a thread libero.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugThreadCall` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Gestisce le chiamate per eseguire il codice in un altro thread.|