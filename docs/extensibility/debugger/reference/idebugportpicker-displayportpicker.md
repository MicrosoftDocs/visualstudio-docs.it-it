---
title: IDebugPortPicker::DisplayPortPicker | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb43ac1bdf173de8e7224f154ecb57cca53abd8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Consente di visualizzare la finestra di dialogo specificata che consente all'utente di selezionare una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hwndParentDialog`  
 [in] Handle di finestra di dialogo padre.  
  
 `pbstrPortId`  
 [out] Stringa dell'identificatore di porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Valore restituito di `S_FALSE` (o valore restituito di `S_OK` con il `BSTR` impostato su `NULL`) indica che l'utente ha fatto clic **Annulla**.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)