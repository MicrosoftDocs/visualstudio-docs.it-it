---
title: Metodo getYear (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>Metodo getYear (Date) (JavaScript)
Ottiene l'anno di una `Date` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce l'anno.  
  
## <a name="remarks"></a>Note  
  
> [!IMPORTANT]
>  Questo metodo è obsoleto e viene fornito solo per la compatibilità. Al suo posto usa il metodo `getFullYear`.  
  
 In [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]e quindi nelle versioni di Internet Explorer a partire da [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], il valore restituito è l'anno memorizzato meno 1900. Ad esempio, viene restituito l'anno 1899 come -1 e l'anno 2000 viene restituito come 100.  
  
 In [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] tramite [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], la formula varia a seconda dell'anno. Per gli anni 1900 e 1999, il valore restituito è un valore di 2 cifre che rappresenta l'anno stored meno 1900. Per le date di fuori di tale intervallo, viene restituito l'anno a 4 cifre. Ad esempio, 1996 viene restituito come 96 ma 1825 e 2025 vengono restituiti come.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Metodo setYear (Date)](../../javascript/reference/setyear-method-date-javascript.md)