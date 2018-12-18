---
title: Interfaccia IActiveScriptAuthor | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthor-interface"></a>Interfaccia IActiveScriptAuthor
Rappresenta la creazione di servizi, tra cui IntelliSense e le regole di confronto di informazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IActiveScriptAuthor` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Aggiunge il nome di un elemento di livello radice per lo script di creazione dello spazio dei nomi del motore. Oggetto *elemento di livello radice* è un oggetto che può contenere proprietà e metodi e che possono inoltre contenere un'origine evento.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Aggiunge codice scriptlet come figlio del livello radice `IScriptNode` oggetto. Nell'host, il nome completo dello scriptlet può presentare solo due livelli.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Restituisce il set di caratteri di completamento per un contesto di richiesta di completamento.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Restituisce lo scriptlet che ha gli attributi specificati.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Restituisce tipo di informazioni e le posizioni di ancoraggio di un carattere specificato in un blocco di codice. Fornisce informazioni per il membro IntelliSense, gli elenchi globali e suggerimenti relativi ai parametri.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Restituisce informazioni relative alla lingua.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Restituisce il `IScriptNode` radice dell'albero di script dell'autore.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Restituisce gli attributi di testo di scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Restituisce gli attributi di testo di un blocco di script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Restituisce un valore che indica se un carattere specificato deve eseguire il commit di un completamento delle istruzioni dall'applicazione.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizza il testo dello script, aggiunge il testo dello script di creazione del motore di creazione e crea un `IScriptEntry` oggetto che corrisponde al blocco di script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Rimuove un `NamedItem` oggetto dallo spazio dei nomi dello script del motore di creazione.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Rimuove lo script di creazione dello spazio dei nomi di modulo di gestione di una libreria dei tipi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)