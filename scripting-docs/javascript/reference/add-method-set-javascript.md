---
title: Metodo Add (Set) (JavaScript) | Documenti Microsoft
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-set-javascript"></a>Metodo add (Set) (JavaScript)
Aggiunge un nuovo elemento a un set.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Parametri  
 `setObj`  
 Obbligatorio. Oggetto `Set`.  
  
 `value`  
 Obbligatorio. Nuovo elemento dell'oggetto `Set`.  
  
## <a name="remarks"></a>Note  
 Il nuovo elemento può essere di qualsiasi tipo e deve essere univoco. Se si aggiunge un elemento non univoco a `Set`, il nuovo elemento non verrà aggiunto alla raccolta.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto Set e quindi recuperarli.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]