---
title: IDebugPortSupplierDescription2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c15facb38037272dcf2cef4f06d84d835b874012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Consente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per visualizzare il testo all'interno di **informazioni sul trasporto** sezione del **Connetti a processo** la finestra di dialogo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia è implementata da fornitori di porte.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortSupplierDescription2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descrizione e i metadati di descrizione per il fornitore della porta.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll