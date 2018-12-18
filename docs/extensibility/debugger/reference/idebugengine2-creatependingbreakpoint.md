---
title: IDebugEngine2::CreatePendingBreakpoint | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords: IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 63a6f400f62f61e94b7b43e781f739dfa5f78d29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crea un punto di interruzione in sospeso nel motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBPRequest`  
 [in] Un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) oggetto che descrive il punto di interruzione in sospeso da creare.  
  
 `ppPendingBP`  
 [out] Restituisce un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) oggetto che rappresenta il punto di interruzione in sospeso.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. In genere restituisce `E_FAIL` se il `pBPRequest` parametro non corrisponde a qualsiasi linguaggio supportato da DE se il `pBPRequest` parametro non è valido o incompleto.  
  
## <a name="remarks"></a>Note  
 Un punto di interruzione in sospeso è essenzialmente una raccolta di tutte le informazioni necessarie per associare un punto di interruzione al codice. Il punto di interruzione in sospeso restituito da questo metodo non è associato al codice fino a quando il [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metodo viene chiamato.  
  
 Per ogni punto di interruzione, l'utente imposta gestore di sessione di debug (SDM) chiama questo metodo in ogni DE associata. È compito DE per verificare che il punto di interruzione sia valido per i programmi in esecuzione in tale DE.  
  
 Quando l'utente imposta un punto di interruzione su una riga di codice, la Germania è libero di associare il punto di interruzione di riga più vicina del documento che corrisponde a questo codice. In questo modo all'utente di impostare un punto di interruzione nella prima riga di un'istruzione su più righe, ma associato l'ultima riga (in cui tutto il codice con attribuito nelle informazioni di debug).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CProgram` oggetto. Implementazione del DE del `IDebugEngine2::CreatePendingBreakpoint` potrebbe quindi inoltrare tutte le chiamate a questa implementazione del metodo in una singola applicazione.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)