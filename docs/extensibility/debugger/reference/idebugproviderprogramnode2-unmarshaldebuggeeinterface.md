---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9ebadbc35ee8752e9f3b985a99155444caff5f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Ottiene un'interfaccia specificata nell'ambito dei processi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `riid`  
 [in] GUID dell'interfaccia da ottenere.  
  
 `ppvObject`  
 [out] Restituisce l'oggetto che implementa l'interfaccia desiderata. [C++] questo può essere convertito direttamente al tipo di interfaccia desiderato. [C#] usare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodo per ottenere l'interfaccia desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato quando il motore di debug è in esecuzione [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] spazio di processo e il programma in fase di debug è in esecuzione nel proprio spazio di processo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)