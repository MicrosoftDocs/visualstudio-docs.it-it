---
title: Metodo toLocaleString (Object) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>Metodo toLocaleString (Object) (JavaScript)
Restituisce una data convertita in una stringa utilizzando le impostazioni locali correnti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `dateObj` qualsiasi `Date` oggetto.  
  
 Il `toLocaleString` metodo restituisce un `String` oggetto che contiene la data nel formato lungo predefinito di impostazioni locali correnti.  
  
-   Per le date comprese tra 1601 e D.C. 1999, la data viene formattata in base alle impostazioni internazionali del Pannello di controllo dell'utente.  
  
-   Per le date di fuori di questo intervallo, il formato predefinito di **toString** viene usato il metodo.  
  
 Ad esempio, negli Stati Uniti, `toLocaleString` restituisce "01/05/96 00:00:00" per il 5 gennaio. In Europa, restituisce "01/05/96 00:00:00" per la stessa data, inserisce il giorno prima del mese come convenzione europea.  
  
> [!NOTE]
>  `toLocaleString`deve essere utilizzato solo per visualizzare i risultati per un utente. non deve mai utilizzato come base per il calcolo all'interno di uno script come il risultato restituito è specifica del computer.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto matrice](../../javascript/reference/array-object-javascript.md)&#124; [Data oggetto](../../javascript/reference/date-object-javascript.md)&#124; [Numero oggetto](../../javascript/reference/number-object-javascript.md)&#124; [Oggetto Object](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)