---
title: IWebAppDiagnosticsObjectInitialization::Initialize | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization::Initialize
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32dab78619635f9603fa33794810deef9685a7d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitializationinitialize"></a>IWebAppDiagnosticsObjectInitialization::Initialize
Inizializza gli oggetti creati con [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  
  
> [!IMPORTANT]
>  [Interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) viene rilevata in activdbg100.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Initialize(        [in, annotation("__in")] HANDLE_PTR hPassedHandle,        [in, annotation("__in")] IUnknown* pDebugApplication        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `hPassedHandle`  
 L'handle è stato passato il [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) metodo il `hPassToObject` parametro.  
  
 `pDebugApplication`  
 L'applicazione PDM con cui è stato creato l'oggetto.