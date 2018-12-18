---
title: Oggetto Uint8ClampedArray (JavaScript) | Documenti Microsoft
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="uint8clampedarray-object-javascript"></a>Oggetto Uint8ClampedArray (JavaScript)
Matrice tipizzata di valori Unsigned Integer a 8 bit con valori fissati sull'intervallo 0-255. Il contenuto viene inizializzato a 0. Se non è possibile allocare il numero di byte richiesto, viene generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametri  
 `uint8ClampedArray`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Uint8ClampedArray` è assegnato.  
  
 `length`  
 Facoltativo. Numero di elementi nella matrice.  
  
 `array`  
 Facoltativo. Matrice o matrice tipizzata contenuta in questa matrice. Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo `Uint8`.  
  
 `buffer`  
 Parametro facoltativo. Il [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) che il `Uint8ClampedArray` rappresenta.  
  
 `byteOffset`  
 Parametro facoltativo. Offset in byte dall'inizio del buffer da cui deve iniziare `Uint8ClampedArray`.  
  
 `length`  
 Facoltativo. Numero di elementi nella matrice.  
  
## <a name="remarks"></a>Note  
 I valori archiviati in un oggetto `Uint8ClampedArray` sono compresi tra 0 e 255. Se si imposta un valore negativo per un membro di matrice, il valore impostato è 0. Se si imposta un valore maggiore di 255, il valore impostato è 255.  
  
 I valori in un `Uint8ClampedArray` oggetto vengono arrotondati per il più vicino valore pari, che viene chiamato l'arrotondamento.  
  
## <a name="constants"></a>Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8ClampedArray`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8ClampedArray`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Sola lettura. Ottiene il [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) a cui fa riferimento la matrice.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Sola lettura. La lunghezza di questa matrice dall'inizio del relativo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Sola lettura. L'offset di questa matrice dall'inizio del relativo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), in byte, fissata in fase di costruzione.|  
|[Proprietà Length](../../javascript/reference/length-property-uint8clampedarray.md)|Lunghezza della matrice.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint8ClampedArray`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set](../../javascript/reference/set-method-uint8clampedarray.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Ottiene un nuovo `Uint8ClampedArray` visualizzare il [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) archiviare per questa matrice, specificando il primo e l'ultimo elemento della sottomatrice.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come usare un oggetto `Uint8ClampedArray` per elaborare i dati binari acquisiti da `XmlHttpRequest`:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra in che modo i valori vengono limitati in `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra in che modo i valori vengono arrotondati in `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)
