---
title: Interfaccia IProcessDebugManager | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanager-interface"></a>Interfaccia IProcessDebugManager
Interfaccia principale per la gestione di debug del processo. Questa interfaccia può creare, aggiungere o rimuovere un'applicazione virtuale da un processo. È possibile enumerare gli stack frame e thread dell'applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IProcessDebugManager` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crea un nuovo oggetto di applicazione di debug per questa applicazione.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Restituisce un oggetto di applicazione predefinito per il processo corrente.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Aggiunge un'applicazione all'elenco del gestore di machine debug delle applicazioni in esecuzione.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Rimuove l'esecuzione di un'applicazione elenco di applicazioni.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crea un nuovo helper di documento di debug per questa applicazione.|