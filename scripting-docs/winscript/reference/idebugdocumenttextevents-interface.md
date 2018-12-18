---
title: Interfaccia IDebugDocumentTextEvents | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextevents-interface"></a>Interfaccia IDebugDocumentTextEvents
Fornisce gli eventi che indicano le modifiche apportate al documento di testo associata.  
  
> [!NOTE]
>  Il testo del documento viene modificato quando gli eventi su questa interfaccia vengono attivati. I gestori di eventi possono recuperare il testo utilizzando il `IDebugDocumentText` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugDocumentTextEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica che il documento sottostante è stata distrutta e non è più valido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica che è stato aggiunto il nuovo testo al documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica che il testo è stato rimosso dal documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica che è stato sostituito il testo.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica che gli attributi di testo associati all'intervallo di posizione di carattere sottostante sono stati modificati.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica che gli attributi del documento modificata.|