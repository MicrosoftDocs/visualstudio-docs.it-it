---
title: IActiveScript | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
Fornisce i metodi necessari per inizializzare il motore di script. Il motore di script deve implementare il `IActiveScript` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Segnala al motore di scripting di [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornito dall'host al sito.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera l'oggetto sito associato con il motore di Script di Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Inserisce lo stato specificato il motore di script.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera lo stato corrente del motore di scripting.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Fa sì che il motore di script per l'abbandono di tutti gli script caricati, perdono il proprio stato e rilasciare qualsiasi puntatori a interfaccia che dispone di altri oggetti, quindi immettere uno stato chiuso.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Aggiunge il nome di un elemento di livello radice allo spazio dei nomi del motore di script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera il `IDispatch` interfaccia per l'esecuzione dello script.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificatore script-modulo di gestione-definito per il thread attualmente in esecuzione.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificatore script-modulo di gestione-definito per il thread associato al thread Win32 Microsoft specificato.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera lo stato corrente di un thread di script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompe l'esecuzione di un thread in esecuzione di script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona il motore di script corrente (meno qualsiasi stato corrente dell'esecuzione), la restituzione di un motore di script caricato che non dispone di alcun sito nel thread corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)