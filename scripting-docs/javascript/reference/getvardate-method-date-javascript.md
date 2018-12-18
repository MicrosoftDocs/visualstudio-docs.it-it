---
title: Metodo getVarDate (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>Metodo getVarDate (Date) (JavaScript)
Restituisce un valore VT_DATE da un oggetto `Date` .  
  
> [!WARNING]
>  Questo metodo è supportato solo in Internet Explorer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore VT_DATE.  
  
## <a name="remarks"></a>Note  
 Il metodo `getVarDate` viene usato quando il codice JavaScript interagisce con oggetti COM, oggetti ActiveX o altri oggetti che accettano e restituiscono i valori di data in formato VT_DATE. Tra questi, gli oggetti in Visual Basic e Visual Basic, Scripting Edition (VBScript). Il formato effettivo del valore restituito dipende dalle impostazioni internazionali.  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Funzione Date.parse](../../javascript/reference/date-parse-function-javascript.md)