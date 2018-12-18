---
title: IDebugDocumentContext2::GetStatementRange | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetStatementRange
helpviewer_keywords: IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 942e8172c337621701ba827ba18b46bf3f6d7c88
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Ottiene l'intervallo dei file di istruzione del contesto del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetStatementRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBegPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che viene compilato con la posizione iniziale. Impostare questo argomento per un valore null se tali informazioni non sono necessarie.  
  
 `pEndPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che viene compilato con la posizione finale. Impostare questo argomento per un valore null se tali informazioni non sono necessarie.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un intervallo di istruzione è l'intervallo di righe che hanno contribuito il codice a cui fa riferimento questo contesto di documento.  
  
 Per ottenere l'intervallo del codice sorgente (inclusi commenti) all'interno di questo contesto di documento, chiamare il [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CDebugContext` oggetto che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia. In questo esempio viene compilata la posizione finale solo se la posizione di inizio non è un valore null.  
  
```cpp  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)