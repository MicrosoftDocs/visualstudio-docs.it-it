---
title: Oggetto Uint8Array | Documenti Microsoft
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72002af4ca92d1104a3c3c3bb2339e63856a80a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="uint8array-object"></a>Oggetto Uint8Array
Matrice tipizzata di Integer a 8 bit senza segno. Il contenuto viene inizializzato a 0. Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parametri  
 `uint8Array`  
 Obbligatorio. Il nome della variabile a cui il **Uint8Array** oggetto è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice. Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Uint8.  
  
 `buffer`  
 ArrayBuffer rappresentato da Uint8Array.  
  
 `byteOffset`  
 Parametro facoltativo. Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Uint8Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## <a name="constants"></a>Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8array.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8Array`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint8array.md)|Sola lettura. Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint8array.md)|Sola lettura. Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint8array.md)|Sola lettura. Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà Length](../../javascript/reference/length-property-uint8array.md)|Lunghezza della matrice.|  
|||  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint8Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set (Uint8Array)](../../javascript/reference/set-method-uint8array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray (Uint8Array)](../../javascript/reference/subarray-method-uint8array.md)|Ottiene una nuova visualizzazione Uint8Array dell'archivio ArrayBuffer per questa matrice.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Uint8Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]