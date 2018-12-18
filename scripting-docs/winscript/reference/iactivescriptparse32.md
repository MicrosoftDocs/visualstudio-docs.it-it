---
title: IActiveScriptParse32 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Se lo Script di Windows motore consente gli scriptlet codice di testo non elaborato da aggiungere allo script oppure testo dell'espressione da valutare in fase di esecuzione, implementa la `IActiveScriptParse32` interfaccia. Nei linguaggi di scripting interpretati che non dispongono di alcun ambiente di creazione indipendente, come VBScript, si fornisce un meccanismo alternativo (diverso da `IPersist*`) per ottenere il codice di script nel motore di scripting e associare i frammenti di script per oggetti diversi eventi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Aggiunge codice scriptlet allo script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inizializza il motore di script.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizza lo scriptlet codice specifico, aggiungendo le dichiarazioni nello spazio dei nomi e la valutazione di codice nel modo appropriato.|