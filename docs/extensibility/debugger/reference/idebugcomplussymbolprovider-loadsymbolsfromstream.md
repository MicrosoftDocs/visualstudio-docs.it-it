---
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 155efd9e51d8fec2a617b46a1dd069d41dc5849c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Carica simboli il flusso di dati di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LoadSymbolsFromStream(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStream(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore del dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco del modulo.  
  
 `baseAddress`  
 [in] Indirizzo di base di memoria.  
  
 `pUnkMetadataImport`  
 [in] Oggetto che contiene i metadati del simbolo.  
  
 `pStream`  
 [in] Flusso di dati che contiene i simboli.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone il [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia. Le chiamate al metodo di [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) metodo.  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IStream* pStream  
)  
{  
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)