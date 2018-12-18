---
title: Interfaccia IPerPropertyBrowsing2 1 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>Interfaccia IPerPropertyBrowsing2 1
Accede alle informazioni nelle pagine delle proprietà offerto da un oggetto.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetDisplayString`|Restituisce una stringa di testo che descrive la proprietà specificata.|  
|`MapPropertyToPage`|Restituisce il CLSID della pagina delle proprietà che consente la modifica della proprietà specificata.|  
|`GetPredefinedStrings`|Restituisce una matrice di stringhe conteggiata (`LPOLESTR` puntatori) Elenca le descrizioni dei valori consentiti in grado di accettare la proprietà specificata.|  
|`SetPredefinedValue`|Imposta il valore della proprietà sul valore predefinito identificato dal token`dwCookie.`|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dbgprop.h