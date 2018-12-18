---
title: Metodo findIndex (Array) (JavaScript) | Documenti Microsoft
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="findindex-method-array-javascript"></a>Metodo findIndex (Array) (JavaScript)
Restituisce un valore di indice per il primo elemento della matrice che soddisfa i criteri di test specificati in una funzione di callback.  
  
## <a name="syntax"></a>Sintassi  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto array.  
  
 `callbackfn`  
 Obbligatorio. La funzione di callback per testare ogni elemento nella matrice.  
  
 `thisArg`  
 Parametro facoltativo. Specifica l'oggetto `this` nella funzione di callback. Se non è specificato, l'oggetto `this` è non definito.  
  
## <a name="remarks"></a>Note  
 Il metodo `findIndex` chiama la funzione di callback una volta per ogni elemento nella matrice, in ordine crescente, finché non viene restituito `true`. Non appena un elemento restituisce true, `findIndex` restituisce il valore di indice dell'elemento che restituisce true. Se nessun elemento nella matrice restituisce true, `findIndex` restituisce -1.  
  
 `findIndex` non modifica l'oggetto array.  
  
## <a name="callback-function-syntax"></a>Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, thisArg)`  
  
 È possibile dichiarare la funzione di callback usando un massimo di tre parametri.  
  
 I parametri della funzione di callback sono i seguenti.  
  
|Argomento di callback|Definizione|  
|-----------------------|----------------|  
|`value`|Valore dell'elemento di matrice.|  
|`index`|Indice numerico dell'elemento di matrice.|  
|`arrayObj`|Oggetto array da attraversare.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente la funzione di callback verifica se ogni elemento della matrice è uguale a 2.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa la sintassi freccia per testare ogni elemento. In questo esempio, nessun elemento restituisce `true`, e `findIndex` restituisce -1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]