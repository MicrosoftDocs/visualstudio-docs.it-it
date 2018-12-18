---
title: IDebugComPlusSymbolProvider2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 543af641d5bad8d07b3ed0d6cb3b8539395991f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Rappresenta un provider di simboli COM+ con metodi specifici al codice gestito ed estende il **IDebugComPlusSymbolProvider**[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Determina se il metodo specificato ha informazioni sulla riga.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera un tipo di dato il relativo nome.|  
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Recupera un tipo di dato il relativo token.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Determina se l'indirizzo di debug specificata è un punto di sequenza.|  
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Carica i simboli utilizzando il metodo di callback specificato di debug.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Caricare i simboli di debug da un flusso di dati specificato di **ICorDebugModule** oggetto.|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Carica i simboli di debug di **ICorDebugModule** oggetto.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll