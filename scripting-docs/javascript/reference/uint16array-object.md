---
title: Oggetto Uint16Array | Documenti Microsoft
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="uint16array-object"></a>Oggetto Uint16Array
Matrice tipizzata di valori unsigned integer a 16 bit. Il contenuto viene inizializzato a 0. Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Parametri  
 `uint16Array`  
 Obbligatorio. Il nome della variabile a cui il **Uint16Array** oggetto è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice. Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Uint16.  
  
 `buffer`  
 ArrayBuffer rappresentato da Uint16Array.  
  
 `byteOffset`  
 Parametro facoltativo. Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Uint16Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## <a name="constants"></a>Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint16Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint16Array`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint16array.md)|Sola lettura. Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint16array.md)|Sola lettura. Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint16array.md)|Sola lettura. Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà Length](../../javascript/reference/length-property-uint16array.md)|Lunghezza della matrice.|  
|||  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint16Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Ottiene una nuova visualizzazione Uint16Array dell'archivio ArrayBuffer per questa matrice.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Uint16Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]