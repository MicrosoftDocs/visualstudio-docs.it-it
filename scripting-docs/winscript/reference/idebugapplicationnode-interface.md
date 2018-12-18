---
title: Interfaccia IDebugApplicationNode | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>Interfaccia IDebugApplicationNode
Il `IDebugApplicationNode` interfaccia estende la funzionalità del `IDebugDocumentProvider` interfaccia fornendo un contesto all'interno di un albero di progetto.  
  
 Oltre ai metodi ereditati da `IDebugDocumentProvider`, `IDebugApplicationNode` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Enumera i nodi figlio del nodo dell'applicazione.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Restituisce il nodo padre del nodo dell'applicazione.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Imposta il provider di documento per il nodo dell'applicazione.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Fa sì che l'applicazione per rilasciare tutti i riferimenti e immettere uno stato inattivo.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Aggiunge il nodo dell'applicazione per la struttura del progetto specificato.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Rimuove il nodo dell'applicazione dalla struttura del progetto.|