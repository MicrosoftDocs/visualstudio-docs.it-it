---
title: Interfaccia IActiveScriptParseProcedureOld | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfaccia IActiveScriptParseProcedureOld
Consente il testo del codice sorgente per le procedure da aggiungere allo script. Interpretato linguaggi di script che non dispongono di un ambiente di creazione indipendente, come VBScript, si fornisce un meccanismo alternativo (diverso da `IActiveScriptParse` o `IPersist*`) per aggiungere lo spazio dei nomi delle procedure di script.  
  
> [!NOTE]
>  Questa interfaccia è deprecata a favore del `IActiveScriptParseProcedure` interfaccia.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, `IActiveScriptParseProcedureOld` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizza la routine di codice specificato e aggiunge la procedura per lo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)