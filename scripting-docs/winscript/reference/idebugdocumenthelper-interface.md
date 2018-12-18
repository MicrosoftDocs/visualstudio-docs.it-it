---
title: Interfaccia IDebugDocumentHelper | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>Interfaccia IDebugDocumentHelper
Fornire le implementazioni per molte delle interfacce necessarie per l'hosting intelligente, ad esempio il `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, e `IDebugDocumentTextEvents` interfacce.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugDocumentHelper` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Inizializza un helper del documento di debug con un nome e attributi iniziali.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Questo documento aggiunto all'albero del documento.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Rimuove l'albero del documento di questo documento.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Aggiunge una stringa Unicode alla fine di questo documento.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Aggiunge una stringa DBCS alla fine di questo documento.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Imposta il `IDebugDocumentHost` per questo documento.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Notifica l'helper che il testo specificato è disponibile, ma non fornisce i caratteri.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Indica l'helper che un determinato intervallo di caratteri è un blocco di script gestito dal motore di script specificato.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Imposta gli attributi predefiniti da utilizzare per il testo che non è in un blocco di script.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Imposta gli attributi in un intervallo di testo.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Imposta il nome lungo per il documento.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Imposta il nome breve per il documento.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Imposta gli attributi per questo documento.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Restituisce il nodo debug dell'applicazione corrispondente a questo documento.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Recupera l'intervallo di caratteri e il motore di script corrispondente a un blocco di script.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Crea un nuovo contesto di documento di debug.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Porta il documento verso l'alto nel debugger di interfaccia utente.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Inserisce un contesto di questo documento nella parte superiore nell'interfaccia utente del debugger.|