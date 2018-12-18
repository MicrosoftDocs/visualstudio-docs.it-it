---
title: Funzione String.Raw (JavaScript) | Documenti Microsoft
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>Funzione String.raw (JavaScript)
Restituisce il formato di stringa non elaborata di una stringa di modello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Parametri  
 `templateStr`  
 Obbligatorio. Stringa di modello.  
  
 `obj`  
 Obbligatorio. Oggetto ben formato specificato usando la notazione del valore letterale di oggetto, ad esempio { raw: 'valore' }.  
  
 `...substitutions`  
 Parametro facoltativo. Una matrice (un [parametro rest](../../javascript/functions-javascript.md)) composta da uno o più valori di sostituzione.  
  
## <a name="remarks"></a>Note  
 Il `String.raw` funzione viene utilizzata per l'utilizzo con [stringhe di modello](../../javascript/advanced/template-strings-javascript.md). La stringa non elaborata includerà qualsiasi carattere di escape e barra rovesciata presenti nella stringa.  
  
 Viene generato un errore se `obj` non è un oggetto ben formato.  
  
## <a name="example"></a>Esempio  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]