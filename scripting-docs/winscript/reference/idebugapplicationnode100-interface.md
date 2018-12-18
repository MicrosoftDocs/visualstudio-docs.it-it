---
title: Interfaccia IDebugApplicationNode100 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>Interfaccia IDebugApplicationNode100
Il `IDebugApplicationNode100` interfaccia estende la funzionalità del [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). È possibile ottenere un'istanza di questa interfaccia tramite la chiamata QueryInterface su un'implementazione di [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v di 10.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplicationNode100` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ottiene i documenti di testo che sono nascosti per il filtro specificato.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Imposta il filtro in un particolare [interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementazione. In questo modo il debugger di script filtrare i nodi figlio generato dal compilatore di applicazioni in modo da PDM non invierà più gli eventi quando i nodi vengono creati o rimossi. Per impostazione predefinita, verranno inviati tutti i nodi.|