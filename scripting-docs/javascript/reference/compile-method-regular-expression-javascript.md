---
title: Metodo Compile (Regular Expression) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>Metodo compile (Regular Expression) (JavaScript)
Compila un'espressione regolare in un formato interno per velocizzare l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Parametri  
 `rgExp`  
 Obbligatorio. Un'istanza di un **espressione regolare** oggetto. Può essere un nome di variabile o un valore letterale.  
  
 *modello*  
 Obbligatorio. Un'espressione stringa contenente un criterio di espressione regolare da compilare  
  
 `flags`  
 Parametro facoltativo. I flag disponibili, che possono essere combinati, sono:  
  
-   g (ricerca globale per tutte le occorrenze di *modello*)  
  
-   i (ignora maiuscole/minuscole)  
  
-   m (ricerca su più righe)  
  
## <a name="remarks"></a>Note  
 Il **compilare** metodo converte *modello* in un formato interno per velocizzare l'esecuzione. In questo modo, ad esempio per un utilizzo più efficiente delle espressioni regolari nei cicli. Un'espressione regolare compilata di velocizzare operazioni se si riutilizza ripetutamente la stessa espressione. Non offre alcun vantaggio non viene acquisita, tuttavia, se l'espressione regolare viene modificato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **compilare** metodo:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)