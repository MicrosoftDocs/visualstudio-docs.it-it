---
title: IDebugArrayObject::GetElement | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElement
helpviewer_keywords: IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dbe40cd481d3044eb87b5c5935e023bc7b110a50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Ottiene un elemento della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwIndex`  
 [in] L'indice dell'elemento.  
  
 `ppElement`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia che rappresenta l'elemento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo visualizza tutti gli elementi di un oggetto matrice come una matrice unidimensionale, anche se l'oggetto di matrice è multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]` e un `dwIndex` parametro pari a 20, questo metodo deve restituire l'elemento da `myarray[1][1][2]`e un `dwIndex` parametro 21 deve restituire l'elemento da `myarray[1][1][3]`. Utilizzare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodo per determinare il numero totale di elementi nella matrice.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)