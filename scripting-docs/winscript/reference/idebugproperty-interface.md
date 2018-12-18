---
title: Interfaccia IDebugProperty | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>Interfaccia IDebugProperty
Utilizzata per descrivere le proprietà gerarchico dell'entità in fase di debug che ha un nome, tipo e valore. In genere, `IDebugProperty` viene utilizzato per descrivere il risultato della valutazione dell'espressione, la valutazione di istruzione o evaluation di registro.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi del `IDebugProperty` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Ottenere il `DebugPropertyInfo` che descrive l'oggetto`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ottiene le informazioni su una proprietà estese.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Enumera i membri di una proprietà.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ottiene l'elemento padre di una proprietà.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dbgprop.h