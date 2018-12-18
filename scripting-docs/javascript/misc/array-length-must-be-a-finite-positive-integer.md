---
title: La lunghezza della matrice deve essere un integer positivo finito | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La lunghezza della matrice deve essere pari a un valore integer positivo finito
Si sta chiamando il **matrice** costruttore con un argomento che non è un numero intero (numeri interi sono costituiti da zero e l'insieme di numeri interi positivi).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Utilizzare numeri interi positivi solo quando si crea un nuovo `Array` oggetto. Se si desidera creare una matrice con un unico elemento che non è un numero intero, è possibile eseguire questa operazione in un processo in due passaggi. Prima di creare una matrice con un elemento, quindi inserire il valore nel primo elemento (array[0]). Di seguito è riportato un esempio che genera l'errore.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Nell'esempio seguente viene illustrato il modo corretto per specificare una matrice con un solo elemento numerico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Non è previsto alcun limite superiore per le dimensioni di una matrice, diverso dal valore del numero intero massimo (circa 4 miliardi).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)