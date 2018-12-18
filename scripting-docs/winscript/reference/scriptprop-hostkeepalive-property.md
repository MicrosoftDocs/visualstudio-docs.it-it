---
title: "Proprietà SCRIPTPROP_HOSTKEEPALIVE | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptprophostkeepalive-property"></a>Proprietà SCRIPTPROP_HOSTKEEPALIVE
Consente di specificare se il motore di script deve essere mantenuto completamente funzionale se sono presenti riferimenti in sospeso.  
  
 Utilizzare [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) per impostare questa proprietà su `true`. Se questa proprietà è impostata su `true`, il motore di script viene mantenuto completamente funzionale, purché vi sia almeno un riferimento in sospeso per il motore di script o per un `IDispatch` puntatore a un oggetto JavaScript creato tramite la creazione di script motore. Quando questa proprietà è impostata su `true`, è consigliabile non esplicitamente chiudere o reimpostare il motore di script tramite il [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) o [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metodi. La versione dell'ultimo riferimento a un oggetto script si arresta il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Requisiti  
 Questa proprietà viene visualizzata solo nella versione di activscp.idl che viene installato con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con 2707082 KB per Internet Explorer 8 in [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o con 2722913 KB per Internet Explorer 9 in [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].