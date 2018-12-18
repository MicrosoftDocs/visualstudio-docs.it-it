---
title: IDebugDocumentChecksum2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 068447399a8cfd43cb5fe07ea82e7cf4400f460c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Rappresenta un checksum per un documento di debug e consente di passare il valore di checksum tra i componenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia può essere implementata da qualsiasi componente che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia. Tuttavia, viene principalmente implementato dai motori di debug in modo che il valore di checksum incorporato in un file di simboli (PDB) può essere passato nuovamente all'IDE e utilizzato durante la ricerca di un'origine.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentChecksum2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera l'identificatore di checksum e l'algoritmo del documento con il numero massimo di byte da utilizzare.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll