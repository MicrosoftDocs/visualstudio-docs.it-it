---
title: IDebugDocumentContext2::Compare | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::Compare
helpviewer_keywords: IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 550695aa52f1c913b25fc56975eb5c6e36b4c091
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto di documento in una matrice specificata di contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `compare`  
 [in] Un valore di [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumerazione che specifica il tipo di confronto.  
  
 `rgpDocContextSet`  
 [in] Matrice di [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) gli oggetti che rappresentano i contesti di documento da confrontare.  
  
 `dwDocContextSetLen`  
 [in] La lunghezza della matrice di contesti di documento da confrontare.  
  
 `pdwDocContext`  
 [out] Restituisce l'indice nel `rgpDocContextSet` matrice del primo contesto di documento che soddisfa il confronto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) gli oggetti passati nella matrice devono essere implementati dallo stesso motore di debug che implementa il `IDebugDocumentContext2` oggetto chiamato; in caso contrario, il confronto non è valido.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)