---
title: IEEDataStorage::GetData | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage::GetData
helpviewer_keywords: IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e18b51c20d2eaf324782574bf007ce32fdc6df2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera il numero specificato di byte dall'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataSize`  
 [in] Il numero di byte da recuperare (il `data` matrice deve contenere almeno questo numero di byte).  
  
 `sizeGotten`  
 [out] Restituisce il numero di byte effettivamente recuperati.  
  
 `data`  
 [in, out] Matrice da riempire con i dati richiesti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'utilizzo di questo metodo consigliato consiste nel recuperare tutti i byte di dati in una matrice locale, poiché non esiste alcun modo per ignorare i byte nel processo di recupero. In questo caso, il parametro `dataSize` dovrebbe essere il valore restituito dal [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)