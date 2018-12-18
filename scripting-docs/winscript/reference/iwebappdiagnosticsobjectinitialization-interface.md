---
title: Interfaccia IWebAppDiagnosticsObjectInitialization | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 159b81a336accea4e4e8c035119d5525de71ae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>Interfaccia IWebAppDiagnosticsObjectInitialization
Questa interfaccia può essere implementata nelle classi che implementano [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata dall'oggetto che implementa [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Nella maggior parte dei casi questo oggetto è PDM.  
  
 Dopo l'oggetto è stato creato, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e `hPassToObject` parametro di `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization`viene rilevata in activdbg100.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inizializza l'oggetto.|