---
title: IDebugDocumentPositionOffset2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 12b3d9781348beb69bb2f4923dd5d5b311f157c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Rappresenta una posizione in un file di origine come un offset di carattere.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Implementata dall'IDE e utilizzato dai motori di debug.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentPositionOffset2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera l'intervallo per la posizione del documento corrente.|  
  
## <a name="remarks"></a>Note  
 Restituisce le stesse informazioni [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma in `char` viene eseguito l'offset dall'inizio del documento. Ad esempio sarebbe infatti disponibile su un disco, vale a dire una matrice unidimensionale di caratteri, anziché le informazioni di riga e colonna che viene restituito in genere, questo presenta il documento.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)