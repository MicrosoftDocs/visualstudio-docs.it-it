---
title: Interfaccia IWebAppDiagnosticsSetup | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfaccia IWebAppDiagnosticsSetup
Questa interfaccia viene implementata da un'applicazione di debug PDM per creare oggetti COM nel processo sottoposto a debug e per abilitare la diagnostica di web. Se PDM esegue il debug dell'applicazione oggetto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer chiama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) dopo che è stato creato e passa un riferimento a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Un'applicazione WWA chiama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) e passa il WWA interfaccia IWebApplicationHost invece. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato con un valore non NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce true. Se non, restituisce false e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`è implementata da PDM v 11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ottiene i documenti di testo che sono nascosti per il filtro specificato.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|