---
title: IActiveScriptSite | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementato dall'host per creare un sito per il motore di Script di Windows. In genere, questo sito sarà associato al contenitore di tutti gli oggetti che sono visibili agli script (ad esempio, i controlli ActiveX). In genere, questo contenitore corrisponderà al documento o pagina visualizzata. Microsoft Internet Explorer, ad esempio, è necessario creare tale un contenitore per ogni pagina HTML visualizzata. Ogni ActiveX controllo (o un altro oggetto di automazione) nella pagina e il motore di script, sarebbe enumerabile all'interno del contenitore.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera l'identificatore delle impostazioni locali utilizzati dall'host per la visualizzazione di elementi dell'interfaccia utente.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ottiene informazioni su un elemento che è stato aggiunto a un modulo tramite una chiamata al [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metodo.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una stringa definita dall'host che identifica in modo univoco la versione corrente del documento dal punto di vista dell'host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chiamata eseguita quando lo script ha completato l'esecuzione.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Comunica all'host che il motore di script è stato modificato gli stati.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Comunica all'host che si è verificato un errore di esecuzione durante l'esecuzione il motore di script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Comunica all'host che il motore di script ha iniziato a eseguire il codice di script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Comunica all'host che il motore di script ha restituito dall'esecuzione di codice di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)