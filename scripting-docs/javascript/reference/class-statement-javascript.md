---
title: Istruzione Class (JavaScript) | Documenti Microsoft
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="class-statement-javascript"></a>Istruzione class (JavaScript)
Dichiara una nuova classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Parametri  
 `classname`  
 Obbligatorio. Nome della classe.  
  
 `object`  
 Parametro facoltativo. Un oggetto o una classe da cui la nuova classe eredita le proprietà e metodi.  
  
 `constructor`  
 Parametro facoltativo. Una funzione costruttore che inizializza la nuova istanza della classe.  
  
 `arg1...argN`  
 Parametro facoltativo. Un elenco facoltativo delimitato da virgole degli argomenti che la funzione è in grado di comprendere.  
  
 `statements`  
 Parametro facoltativo. Una o più istruzioni [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Parametro facoltativo. Specifica un metodo statico.  
  
 `method`  
 Parametro facoltativo. Una o più [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] istanza o metodi statici che possono essere chiamati su un'istanza della classe.  
  
## <a name="remarks"></a>Note  
 Una classe consente di creare nuovi oggetti usando l'ereditarietà basata su prototipo, costruttori, metodi di istanza e metodi statici. È possibile usare l'oggetto `super` all'interno di un costruttore di classe o un metodo della classe per chiamare il costruttore stesso o un metodo nella classe o nell'oggetto padre. Facoltativamente, usare l'istruzione `extends` dopo il nome della classe per specificare la classe o l'oggetto da cui la nuova classe eredita i metodi.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Esempio  
 È inoltre possibile creare nomi di proprietà calcolati per le classi. Nell'esempio di codice seguente viene creato un nome di proprietà calcolato usando la sintassi `set`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene creato dinamicamente un nome di proprietà per una classe usando la sintassi `get`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]