---
title: IDebugProperty2::GetExtendedInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6865361ac0b518f4fa78a3521973d756e6ab780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Ottiene le informazioni per la proprietà estese.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidExtendedInfo`  
 [in] GUID che determina il tipo di informazioni estese da recuperare. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 `pExtendedInfo`  
 [out] Restituisce un `VARIANT` (C++) o un oggetto (c#) che può essere utilizzato per recuperare le informazioni sulle proprietà estese. Ad esempio, questo parametro è potrebbe restituire un `IUnknown` interfaccia che è possibile eseguire query per un [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaccia. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Restituisce `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se non sono disponibili informazioni estese da recuperare.  
  
## <a name="remarks"></a>Note  
 Questo metodo è disponibile per il recupero delle informazioni che non si prestano a essere recuperato chiamando il [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo.  
  
 Il seguente GUID in genere sono riconosciuti da questo metodo (i valori GUID sono specificati per c#, poiché il nome non è disponibile in qualsiasi assembly). È possibile creare ulteriori GUID per uso interno.  
  
|nome|GUID|Descrizione|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Restituisce un `IUnknown` interfaccia al documento. In genere, il [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaccia può essere ottenuta da questo `IUnknown` interfaccia.|  
|guidCodeContext|{e2fc65e 56ce - 11d 1-b528-00aax004a8797}|Restituisce un `IUnknown` interfaccia per il contesto del documento. In genere, il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia può essere ottenuta da questo `IUnknown` interfaccia.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Restituisce una stringa contenente il CLSID di un visualizzatore personalizzato, in genere implementato tramite un analizzatore di espressioni.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Restituisce un numero a 32 bit che rappresenta il numero di slot desiderato se questa proprietà rappresenta un indirizzo locale del codice gestito.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Restituisce una stringa contenente la firma della variabile associata all'oggetto di proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)