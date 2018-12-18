---
title: Interfaccia IDebugHelper | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelper-interface"></a>Interfaccia IDebugHelper
Funge da factory per i punti di connessione semplice e visualizzatori oggetti. Il gestore di debug di processi (PDM) implementa questa interfaccia, che viene utilizzata dai motori di script.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IDebugHelper` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione dei valori di variante o tipi VARTYPE personalizzata alle stringhe.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Restituisce un'interfaccia di eventi che esegue il wrapping di un determinato `IDispatch` oggetto.|