---
title: IDebugComPlusSymbolProvider | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1eab7e30715032500719ee371011a600d2e9552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109740"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Rappresenta un provider di simboli COM+ con metodi specifici al codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Anche se vi è alcuna separazione tra le interfacce che sono utili per un analizzatore di espressioni (Java EE) e quelli destinati a essere utilizzato da un motore di debug (DE), i metodi seguenti verranno probabilmente interessano solo gli sviluppatori DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols e UpdateSymbols.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina se i simboli di debug vengono caricati per il modulo specificato dato l'identificatore del dominio applicazione.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo dal tipo primitivo specificato.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Esegue il mapping di una posizione del documento nel modulo specificato in una matrice di indirizzi di debug.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera informazioni sul tipo relative nella matrice specificata, data il relativo indirizzo di debug.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera il nome dell'assembly dato il relativo modulo e un dominio applicazione.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera le classi che vengono implementate nel linguaggio di programmazione specificato con l'attributo specificato.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera le classi con l'attributo specificato in un determinato modulo.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera il punto di ingresso dell'applicazione.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera l'indirizzo di una funzione che rappresenta l'offset di riga specificato.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera il layout delle variabili locali per un set di metodi.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Restituisce il nome associato al token specificato, il relativo oggetto di metadati specificato.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera i simboli di debug con l'attributo padre specificato per il modulo specificato.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera il lettore di simboli per essere utilizzato da codice non gestito.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera in un tipo di simbolo dato il relativo indirizzo di debug.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se la funzione in corrispondenza dell'indirizzo di debug specificata viene eliminata.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se la funzione in corrispondenza dell'indirizzo di debug specificata viene considerata non aggiornata.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se il codice in corrispondenza dell'indirizzo di debugger specificato è nascosto.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carica i simboli di debug specificata in memoria.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carica simboli il flusso di dati di debug.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Sostituisce i simboli di debug corrente con quelli del flusso di dati specificato.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Scarica i simboli di debug per il modulo specificato dalla memoria.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aggiorna i simboli di debug in memoria con quelli del flusso di dati specificato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll