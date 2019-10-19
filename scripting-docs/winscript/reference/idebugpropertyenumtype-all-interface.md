---
title: Interfaccia IDebugPropertyEnumType_All | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574308"
---
# <a name="idebugpropertyenumtype_all-interface"></a>Interfaccia IDebugPropertyEnumType_All
Le interfacce `IDebugPropertyEnumType` sono definite in modo che ogni IID possa essere passato come filtro per `IDebugProperty::EnumMembers` durante la richiesta dell'enumeratore appropriato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Restituisce una stringa di testo che descrive il nome|  
  
 Le interfacce seguenti ereditano da `IDebugPropertyEnumType_All` e non hanno metodi aggiuntivi.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)