---
title: Interfaccia IScriptNode | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-interface"></a>Interfaccia IScriptNode
Oggetto che implementa il `IScriptNode` interfaccia rappresenta una pagina Web.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IScriptNode` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica se un oggetto è ancora attivo.|  
|[IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Aggiunge un'istanza figlio `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Aggiunge un scriptlet come istanza figlio di un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina l'albero degli oggetti.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Restituisce l'elemento figlio in corrispondenza dell'indice specificato nel nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Restituisce un valore definito dall'applicazione che viene utilizzato per associare un scriptlet con l'oggetto host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Restituisce l'indice di un oggetto nell'elenco di elementi figlio dell'elemento padre.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Restituisce il linguaggio di scripting utilizzato dal nodo di script corrente.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Restituisce il numero dei nodi figlio di `IScriptNode` oggetto.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Restituisce il `IScriptNode` oggetto che rappresenta l'elemento padre di un oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)