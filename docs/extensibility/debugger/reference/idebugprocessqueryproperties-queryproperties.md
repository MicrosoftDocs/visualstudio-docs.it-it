---
title: IDebugProcessQueryProperties::QueryProperties | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c278e5713432c19eaea1a964534c79522e36500b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Query di questo metodo per i valori di una proprietà specificata del processo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```csharp  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Dimensioni delle matrici contenente le definizioni di proprietà e i valori delle proprietà.  
  
 `dwPropType`  
 [in] Matrice che contiene le definizioni delle proprietà sottoposte a query. I valori possibili sono:  
  
-   PROCESS_PROPERTY_COMMAND_LINE = 1  
  
-   PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
-   PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
 `pvarPropValue`  
 [out] Matrice che contiene i valori delle proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato raramente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)