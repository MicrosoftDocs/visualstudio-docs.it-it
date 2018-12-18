---
title: "Proprietà prototype (Error) | Documenti Microsoft"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-error"></a>Proprietà prototype (Error)
Restituisce un riferimento al prototipo per un errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `error` argomento è il nome di un errore.  
  
 Utilizzare il `prototype` proprietà per fornire un set di funzionalità di base a un errore. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Error` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Error.prototype` e quindi usarla.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti hanno una `prototype` proprietà che è di sola lettura. È possibile aggiungere proprietà e metodi al prototipo, ma l'oggetto non può essere assegnato un prototipo diverso. Tuttavia, gli oggetti definiti dall'utente possono essere assegnati un nuovo prototipo.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]