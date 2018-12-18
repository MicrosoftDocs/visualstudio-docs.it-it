---
title: IActiveScriptParseProcedure | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Se il motore di Script di Windows consente il testo del codice sorgente per le procedure da aggiungere allo script, implementa la `IActiveScriptParseProcedure` interfaccia. Nei linguaggi di scripting interpretati che non dispongono di alcun ambiente di creazione indipendente, come VBScript, si fornisce un meccanismo alternativo (diverso da `IActiveScriptParse` o `IPersist`*) per aggiungere procedure script allo spazio dei nomi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizza la routine di codice specificato e aggiunge la routine allo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)