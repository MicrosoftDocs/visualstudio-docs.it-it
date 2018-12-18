---
title: IEnumCodePaths2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2
helpviewer_keywords: IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3da3fbbc8b7ad7dced8a9767b26859cc1a0de1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Questa interfaccia rappresenta un elenco di percorsi di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di percorsi di codice.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumCodePaths2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un numero specificato di percorsi di codice in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora un numero specificato di percorsi di codice in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ottiene il numero di percorsi di codice in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Un percorso di codice rappresenta una chiamata di punto o una funzione di diramazione in un programma. Un elenco di percorsi di codice rappresenta il percorso tramite cui è eseguito l'esecuzione del codice.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)