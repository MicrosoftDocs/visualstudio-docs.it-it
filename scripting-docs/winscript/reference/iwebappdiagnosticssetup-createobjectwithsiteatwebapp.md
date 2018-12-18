---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Questo metodo crea condiviso il cui ID è passato con la classe `rclsid` utilizzando il `dwClsContext`. Questa operazione è simile al modo in cui [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) works, con la differenza che nel caso di `CreateObjectWithSiteAtWebApp` l'oggetto viene creato in modo asincrono sul thread dell'interfaccia utente dell'applicazione web. L'oggetto specificato dall'ID di classe deve implementare [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Dopo l'oggetto è stato creato, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e `hPassToObject` parametro di `CreateObjectWithSiteAtWebApp`. È possibile utilizzare questo metodo per passare all'App un handle per una pipe anonima che è stata copiata utilizzando [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `rclsid`  
 ID di classe della classe da creare.  
  
 `dwClsContext`  
 Il contesto in cui verrà eseguito il codice. Nella maggior parte dei casi è CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Non usato.  
  
 `hPassToObject`  
 Un valore che verrà passato all'oggetto una volta che viene creato nel thread dell'interfaccia utente, se l'oggetto implementa [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).