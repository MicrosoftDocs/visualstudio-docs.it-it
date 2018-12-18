---
title: Interfaccia IDebugFormatter | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97f95aa1ecb91f6caca187939a79a6f09cd2108f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformatter-interface"></a>Interfaccia IDebugFormatter
Consente a un linguaggio o un IDE per personalizzare la conversione tra tipi VARTYPE e valori VARIANT o stringhe.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugFormatter` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Restituisce una stringa che rappresenta il valore di variante specificato.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Restituisce una variabile VARIANT contenente la stringa specificata.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Restituisce una stringa che rappresenta il valore VARTYPE specificato.|