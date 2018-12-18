---
title: IDebugCustomAttribute::GetAttributeBytes | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords: IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4cde5d8f27c7961e3b9ed7bda34473d755226072
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Ottiene le informazioni sugli attributi come un blob di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppBlob`  
 [in, out] Matrice che viene compilata con i byte di attributo.  
  
 `pdwLen`  
 [in, out] Specifica il numero massimo di byte per restituire il `ppBlob` della matrice e restituisce il numero di byte effettivamente scritti nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Impostare il `ppBlob` attributi di parametro con un valore null per restituire il numero di byte disponibili. Quindi allocare una matrice e passare la matrice in per il `ppBlob` parametro.  
  
 I byte di attributo rappresentano i dati non elaborati dell'attributo personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)