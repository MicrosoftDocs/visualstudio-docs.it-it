---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5706d868f0096d486629c18c3d700349af92cc92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se la diagnostica è supportata in questa applicazione. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato sull'oggetto che implementa questa interfaccia con un valore non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. Se non viene restituito `false` e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.  
  
> [!IMPORTANT]
>  [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) è implementata da PDM v 11.0 e versione successiva. Trovato in activdbg100.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato sull'oggetto che implementa questa interfaccia con un valore non NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. Se non viene restituito `false`e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.