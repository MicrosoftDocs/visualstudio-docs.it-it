---
title: Funzione Symbol. keyfor (JavaScript) | Documenti Microsoft
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
ms.assetid: f0b6f034-6d0a-421c-b1c6-52489411e9a3
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22f671a1ea14ce56c52fccbce75893516a10bcc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="symbolkeyfor-function-javascript"></a>Funzione Symbol.keyFor (JavaScript)
Restituisce la chiave per un simbolo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Symbol.keyFor(sym);  
```  
  
#### <a name="parameters"></a>Parametri  
 `sym`  
 Obbligatorio. Oggetto simbolo.  
  
## <a name="remarks"></a>Note  
 Questo metodo cerca il simbolo nel registro dei simboli globali.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
// Local symbol  
var sym1 = Symbol("desc");  
// Global symbol  
var sym2 = Symbol.for("desc");  
  
console.log(Symbol.keyFor(sym1)):  
console.log(Symbol.keyFor(sym2));  
  
// Output:  
// undefined  
// desc  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]