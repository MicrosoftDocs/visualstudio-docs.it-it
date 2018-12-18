---
title: Metodo setYear (Date) (JavaScript) | Documenti Microsoft
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
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>Metodo setYear (Date) (JavaScript)
Imposta il valore dell'anno di `Date` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio. Per gli anni 1900 e 1999, questo è un valore numerico che rappresenta l'anno meno 1900. Per le date di fuori di tale intervallo, questo è un valore numerico di 4 cifre.  
  
## <a name="remarks"></a>Note  
 Questo metodo è obsoleto e viene mantenuto per le versioni precedenti di compatibilità. Al suo posto usa il metodo `setFullYear`.  
  
 Per impostare l'anno di una `Date` oggetto 1997, chiamata **setYear (97)**. Per impostare l'anno 2010, chiamare **setYear (2010)**. Infine, per impostare l'anno in un anno compreso nell'intervallo tra 0 e 99, utilizzare il `setFullYear` metodo.  
  
> [!NOTE]
>  Per [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versione 1.0, `setYear` utilizza un valore che rappresenta il risultato della somma di 1900 al valore dell'anno specificato da `numYear`, indipendentemente dal valore dell'anno. Ad esempio, per impostare l'anno a 1899 `numYear` è -1 e per impostare l'anno 2000 `numYear` è 100.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo getYear (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [Metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)