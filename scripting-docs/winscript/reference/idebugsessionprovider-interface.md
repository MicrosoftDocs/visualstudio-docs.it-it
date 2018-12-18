---
title: Interfaccia IDebugSessionProvider | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>Interfaccia IDebugSessionProvider
L'interfaccia primaria fornito da un debugger IDE per abilitare l'host e della lingua ha avviato il debug. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata dal gestore di debug macchina.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugSessionProvider` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|