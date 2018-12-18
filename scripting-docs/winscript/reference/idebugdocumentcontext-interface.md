---
title: Interfaccia IDebugDocumentContext | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 432fbe9de5b1ab19c64ae1b9eeee36f3b1156d06
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontext-interface"></a>Interfaccia IDebugDocumentContext
Fornisce una rappresentazione astratta di una parte del documento in fase di debug. Per i documenti di testo, questa rappresentazione è costituito da un intervallo di posizione del carattere.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugDocumentContext` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Restituisce il documento che contiene questo contesto.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Enumera i contesti di codice associati al contesto di documento.|