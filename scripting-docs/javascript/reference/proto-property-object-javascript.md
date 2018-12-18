---
title: "__proto__ proprietà (Object) (JavaScript) | Documenti Microsoft"
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
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8659c7a4ece5e30378838f20341ec6712f77ca3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="proto-property-object-javascript"></a>__proto__ proprietà (Object) (JavaScript)
Contiene un riferimento al prototipo interno dell'oggetto specificato.  

> [!WARNING]
> Il `__proto__` proprietà è una caratteristica legacy. Uso [Object. getprototypeof](../reference/object-getprototypeof-function-javascript.md) invece.
  
## <a name="syntax"></a>Sintassi  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto su cui impostare il prototipo.  
  
## <a name="remarks"></a>Note  
 Il `__proto__` proprietà può essere utilizzata per impostare il prototipo per un oggetto.  
  
 L'oggetto o funzione eredita tutti i metodi e proprietà del prototipo, insieme a tutti i metodi e le proprietà nella catena di prototipi del prototipo. Un oggetto può avere solo un singolo prototipo (non inclusi prototipi ereditati nella catena di prototipi), pertanto, quando si chiama il `__proto__` proprietà, si sostituisce il prototipo precedente.  
  
 È possibile impostare il prototipo solo su un oggetto estensibile. Per altre informazioni, vedere [funzione Object. preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Il `__proto__` nome della proprietà inizia e finisce con due caratteri di sottolineatura.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come impostare la proprietà.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come aggiungere proprietà a un oggetto aggiungendoli al prototipo.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente aggiunge il `String` oggetto impostando un nuovo prototipo su di esso.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Prototipi ed ereditarietà](../../javascript/advanced/prototypes-and-prototype-inheritance.md)