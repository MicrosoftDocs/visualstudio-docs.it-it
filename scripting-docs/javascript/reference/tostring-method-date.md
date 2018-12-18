---
title: Metodo toString (Date) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-date"></a>Metodo toString (Date)
Restituisce una rappresentazione di stringa di una data. Il formato della stringa dipende dalle impostazioni locali. Per gli Stati Uniti Inglese (en-us), è come segue:  
  
 *giorno della settimana* *mese* *giorno* *ora*: *minuto*:*secondo* *fuso orario* *anno*  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Parametri  
 `date`  
 Obbligatorio. La data per rappresentare sotto forma di stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce la rappresentazione di stringa della data.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `toString` metodo con una data.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]