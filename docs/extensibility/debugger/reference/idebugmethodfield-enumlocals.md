---
title: IDebugMethodField::EnumLocals | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumLocals
helpviewer_keywords: IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 451c2ccad7d817946bd3d2c2e83ed27279124f2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crea un enumeratore per le variabili locali selezionate del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto che rappresenta l'indirizzo di debug che consente di selezionare il contesto o l'ambito da cui ottenere le variabili locali.  
  
 `ppLocals`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) l'oggetto che rappresenta un elenco di variabili locali; in caso contrario, restituisce un valore null se non sono variabili non locali.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o S_FALSE se sono non presenti variabili locali. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificata. Se sono necessarie tutte le variabili locali incluse le variabili locali generato dal compilatore, chiamare il [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) metodo.  
  
 Un metodo può contenere più contesti di ambito o blocchi. Ad esempio, il metodo seguente ristretto contiene tre ambiti, i due blocchi interni e il corpo del metodo.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 Il [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) oggetto rappresenta il `func` metodo stesso. La chiamata di `EnumLocals` metodo con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) impostato sul `Inner Scope 1` indirizzo restituisce un'enumerazione contenente il `temp1` variabile, ad esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)