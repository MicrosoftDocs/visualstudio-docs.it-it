---
title: Interfaccia IDebugApplicationThreadEvents110 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfaccia IDebugApplicationThreadEvents110
Aggiunge gli eventi di più thread. Questi eventi sono solo locali. Ovvero è possibile sottoscrivere li solo nel processo che viene eseguito il debug, usando il [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) di notifica e annullare gli avvisi per i metodi su oggetti di thread dell'applicazione PDM (oggetti che implementano [IDebugApplicationThread Interfaccia](../../winscript/reference/idebugapplicationthread-interface.md)). Si verificano nel thread di che provenienza.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugActivationThreadEvents110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una chiamata nel thread tramite il thread del PDM cambio è iniziata.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Il thread sta per essere ripresa da un punto di interruzione e sarà attivo ancora una volta.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Il thread è la sospensione di un punto di interruzione e può gestire le chiamate che richiedono il thread completamente da sospendere.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una chiamata nel thread tramite il thread del PDM cambio è stata completata.|