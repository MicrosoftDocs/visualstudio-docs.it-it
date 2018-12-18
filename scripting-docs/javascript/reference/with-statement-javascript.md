---
title: Istruzione with (JavaScript) | Documenti Microsoft
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
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>Istruzione with (JavaScript)
Imposta l'oggetto predefinito per un'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametri  
 `object`  
 Oggetto predefinito.  
  
 `statements`  
 Una o più istruzioni per le quali `object` è l'oggetto predefinito.  
  
## <a name="remarks"></a>Note  
 L'istruzione `with` viene in genere utilizzata per ridurre la quantità di codice necessario in determinate situazioni.  
  
> [!WARNING]
>  L'utilizzo di `with` non è consentito in modalità strict. L'utilizzo di `with` può rendere più difficili la lettura e il debug del codice e deve essere generalmente evitato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente un oggetto `Math` viene utilizzato ripetutamente.  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Esempio  
 Se si riscrive l'esempio per utilizzare l'istruzione `with`, il codice risulterà più conciso:  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione this](../../javascript/reference/this-statement-javascript.md)