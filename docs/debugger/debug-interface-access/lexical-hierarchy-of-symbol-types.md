---
title: Gerarchia lessicale dei tipi di simboli | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6f9fe7b24a1e2bdd68d92f6dd22952df0d2a057
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Gerarchia lessicale dei tipi di simboli
Nella tabella seguente mostra i tipi di simboli nella gerarchia lessicale.  
  
## <a name="symbol-types"></a>Tipi di simboli  
  
|Tipo di simbolo|Descrizione|  
|-----------------|-----------------|  
|[Annotazione](../../debugger/debug-interface-access/annotation.md)|Specifica un percorso con annotazioni nel codice programma.|  
|[Blocco](../../debugger/debug-interface-access/block.md)|Specifica gli ambiti annidati in funzioni.|  
|`Compiland`|Specifica un `compiland` collegato al file .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Specifica i dati di modulo che possono richiedere il caricamento dei dettagli aggiuntivi compilando e pertanto comportano un overhead di run-time per recuperare.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Specifica tutte le variabili di ambiente aggiuntive significative per la compilazione del modulo.|  
|[Custom (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Specifica un simbolo definito dall'utente.|  
|[Dati (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Specifica le variabili come parametri, variabili locali, le variabili globali e i membri di classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Specifica l'ambito globale dei dati. corrisponde a un intero file .exe o DLL.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Specifica una funzione che dispone di un determinato punto al quale il debug è alla fine.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Specifica una funzione che dispone di un determinato punto al quale debug ha inizio.|  
|[Funzione (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Specifica una funzione.|  
|[Etichetta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Specifica una posizione nel codice programma.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Specifica un simbolo esterno che viene visualizzato quando si compila il programma eseguibile.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Specifica un `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Specifica un `namespace`identificatore.|  
  
> [!NOTE]
>  Proprietà dei simboli aggiuntive potrebbero essere disponibili a seconda del tipo di simbolo. Queste proprietà sono elencate negli argomenti di simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)