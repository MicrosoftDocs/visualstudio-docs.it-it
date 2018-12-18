---
title: Oggetto Float32Array | Documenti Microsoft
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
ms.assetid: 4b29456a-1488-4006-ae66-5bf4c05003b1
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f7ef022b43179d2d9ce3f88fc78b8854d3cea62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="float32array-object"></a>Oggetto Float32Array
Matrice tipizzata di valori float a 32 bit. Il contenuto viene inizializzato a 0. Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      float32Array = new Float32Array( length );  
float32Array = new Float32Array( array );  
float32Array = new Float32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametri  
 `float32Array`  
 Obbligatorio. Il nome della variabile a cui il **Float32Array** oggetto è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice. Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Float32.  
  
 `buffer`  
 ArrayBuffer rappresentato da Float32Array.  
  
 `byteOffset`  
 Facoltativo. Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Float32Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## <a name="constants"></a>Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Float32Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-float32array.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Float32Array`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-float32array.md)|Sola lettura. Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-float32array.md)|Sola lettura. Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-float32array.md)|Sola lettura. Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà Length](../../javascript/reference/length-property-float32array.md)|Lunghezza della matrice.|  
|||  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Float32Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Get (metodo)](../../javascript/reference/get-method-float32array.md)|Può essere omesso. Ottiene l'elemento in corrispondenza dell'indice specificato.|  
|[Metodo set (Float32Array)](../../javascript/reference/set-method-float32array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray (Float32Array)](../../javascript/reference/subarray-method-float32array.md)|Ottiene una nuova visualizzazione Float32Array dell'archivio ArrayBuffer per questa matrice.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Float32Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]