---
title: 'Metodo iactivescriptsitetraceinfo:: Sendscripttraceinfo | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5290cc6a92be7c8bc99e4715c77bfe6f8f6abb53
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>Metodo IActiveScriptSiteTraceInfo::SendScriptTraceInfo
Invia le informazioni di traccia che include il tipo di evento, il contesto e l'istruzione di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SendScriptTraceInfo(     [in] SCRIPTTRACEINFO stiEventType,     [in] GUID guidContextID,     [in] DWORD dwScriptContextCookie,     [in] LONG lScriptStatementStart,     [in] LONG lScriptStatementEnd,     [in] DWORD64 dwReserved );   
```  
  
#### <a name="parameters"></a>Parametri  
 `stiEventType`  
 Il tipo di evento.  
  
 `guidContextId`  
 Il GUID del contesto.  
  
 `dwScriptContextCookie`  
 Il cookie del contesto.  
  
 `lScriptStatementStart`  
 La posizione di inizio dell'istruzione dello script.  
  
 `lScriptStatementEnd`  
 Posizione della fine dell'istruzione dello script.  
  
 `dwReserved`  
 Riservato.