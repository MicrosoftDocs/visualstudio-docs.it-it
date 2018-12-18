---
title: IDebugPortPicker | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61973b6b9d7c62e8276f46443d0b9520419d3934
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Rappresenta un'interfaccia utente personalizzata per la selezione della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia è implementata da fornitori di porte. Un fornitore di porta definisce la selezione della porta esporlo come CLSID e scegliendo il `metricPortPickerCLSID` metrica al CLSID esposto.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortPicker`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Consente di visualizzare la finestra di dialogo specificata che consente all'utente di selezionare una porta.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Imposta il provider del servizio.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll