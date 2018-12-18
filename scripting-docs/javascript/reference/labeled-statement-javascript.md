---
title: Un'istruzione (JavaScript) con etichetta | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>Istruzione con etichetta (JavaScript)
Fornisce un identificatore per un'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Parametri  
 *etichetta*  
 Obbligatorio. Identificatore univoco utilizzato per fare riferimento all'istruzione con etichetta.  
  
 `statements`  
 Parametro facoltativo. Uno o più istruzioni associate *etichetta*.  
  
## <a name="remarks"></a>Note  
 Le etichette vengono utilizzate per la **interruzione** e **continuare** istruzioni per specificare l'istruzione in cui il **interruzione** e **continuare** si applicano.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente, il **continuare** istruzione fa riferimento al **per** ciclo che è preceduto dal `Inner:` istruzione. Quando `j` è 24, il **continuare** fa in modo che **per** ciclo all'iterazione successiva. I numeri compresi tra 21 e 23 e 25 e 30 stampa su ogni riga.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)