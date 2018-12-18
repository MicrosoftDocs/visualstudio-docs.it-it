---
title: Oggetto ArrayBuffer | Documenti Microsoft
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>Oggetto ArrayBuffer
Rappresenta un buffer non elaborato di dati binari, usato per archiviare i dati per le diverse matrici tipizzate. `ArrayBuffers`Impossibile leggere o scritti direttamente, ma possono essere passati a una matrice tipizzata o [oggetto DataView](../../javascript/reference/dataview-object.md) per interpretare il buffer non elaborato in base alle esigenze.  
  
 Per ulteriori informazioni sulle matrici tipizzate, vedere [matrici tipizzate](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Parametri  
 `arrayBuffer`  
 Obbligatorio. Nome della variabile a cui l'oggetto `ArrayBuffer` è assegnato.  
  
 `length`  
 La lunghezza del buffer. I contenuti di ArrayBuffer vengono inizializzati a 0. Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `ArrayBuffer`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Sola lettura. La lunghezza di ArrayBuffer (in byte).|  
  
## <a name="functions"></a>Funzioni  
 Nella tabella seguente sono elencate le funzioni dell'oggetto `ArrayBuffer`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Funzione arraybuffer. Isview](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Determina se un oggetto fornisce una visualizzazione del buffer.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `ArrayBuffer`:  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Metodo slice](../../javascript/reference/slice-method-arraybuffer.md)|Restituisce una sezione di un oggetto `ArrayBuffer`.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto ArrayBuffer per elaborare i dati binari acquisiti da un [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). È possibile utilizzare un [oggetto DataView](../../javascript/reference/dataview-object.md) per ottenere i valori singoli.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sull'utilizzo `XmlHttpRequest`, vedere [miglioramenti a XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]