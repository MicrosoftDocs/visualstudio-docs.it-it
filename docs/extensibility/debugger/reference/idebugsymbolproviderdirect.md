---
title: IDebugSymbolProviderDirect | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65a4a2f0f0823b9a723414247e1e1d6eb263d7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Rappresenta un provider di simboli che ha accesso diretto alle interfacce di simbolo di metadati e componenti di base.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera l'identificatore di dominio applicazione con l'indirizzo di debug.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera le informazioni sui moduli nel gruppo di simboli.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera informazioni sul gruppo di simbolo di cui il provider di simbolo è un membro.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera le informazioni di importazione dei metadati.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera informazioni sul metodo in corrispondenza dell'indirizzo di debug specificata.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera un lettore di simboli per codice non gestito.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia consente invece la maggior parte delle altre interfacce di provider di simboli. Fornisce accesso diretto ai metadati e `CorSym` interfacce.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll