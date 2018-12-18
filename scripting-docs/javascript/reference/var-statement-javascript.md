---
title: Istruzione var (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>Istruzione var (JavaScript)
Dichiara una variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Parametri  
 `variable1`  
 Il nome della variabile viene dichiarata.  
  
 `value1`  
 Il valore iniziale assegnato alla variabile.  
  
## <a name="remarks"></a>Note  
 Utilizzare il `var` istruzione per dichiarare le variabili. È possibile assegnare valori alle variabili di dichiarazione o in un secondo momento nello script.  
  
 Una variabile viene dichiarata la prima volta che viene visualizzato nello script.  
  
 È possibile dichiarare una variabile senza utilizzare il `var` (parola chiave) e assegnare un valore a esso. Questo è noto come un *dichiarazione implicita*, e non è consigliata. Una dichiarazione implicita fornisce l'ambito della variabile globale. Quando si dichiara una variabile a livello di routine, tuttavia, in genere si desidera che un ambito globale. Per evitare di assegnare l'ambito della variabile globale, è necessario utilizzare il `var` parola chiave nella dichiarazione della variabile.  
  
 Se non si inizializza la variabile nel `var` istruzione, gli viene assegnato automaticamente il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valore `undefined`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `var` istruzione.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione Function](../../javascript/reference/function-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)