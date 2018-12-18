---
title: Funzione date.Now (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Funzione Date.now (JavaScript)
Ottiene la data e ora correnti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 e la data e ora correnti.  
  
## <a name="remarks"></a>Note  
 Il [metodo getTime](../../javascript/reference/gettime-method-date-javascript.md) restituisce il numero di millisecondi compresi tra 1 gennaio 1970 e una data specificata.  
  
 Per informazioni su come calcolare il tempo trascorso e confrontare le date, vedere [il calcolo di date e ore (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `now`.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Requisiti  
 Non è supportato in versioni precedenti a Internet Explorer 9. Tuttavia, è supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9, standard di Internet Explorer 10. Supportato anche nelle [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date (oggetto)](../../javascript/reference/date-object-javascript.md)   
 [Calcolo di date e ore (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)