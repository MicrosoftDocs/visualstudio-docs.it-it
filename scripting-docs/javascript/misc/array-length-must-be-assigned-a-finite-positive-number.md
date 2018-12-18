---
title: Lunghezza della matrice deve essere assegnato un numero positivo finito | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Alla lunghezza della matrice deve essere assegnato un numero positivo finito
Quando si imposta la **lunghezza** proprietà di un oggetto esistente **matrice** oggetto, è specificata una lunghezza della matrice che non è un numero positivo o zero. Questo errore si verifica quando si assegna un valore per il **lunghezza** proprietà di un `Array` oggetto è negativo o non numerico (`NaN`). Si noti che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte automaticamente i numeri frazionari in valori integer.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Assegnare un numero intero positivo per la proprietà length. Non è previsto alcun limite superiore per le dimensioni di una matrice, diverso dal valore del numero intero massimo (circa 4 miliardi). Nell'esempio seguente viene illustrato il modo corretto per impostare il **lunghezza** proprietà di un **matrice** oggetto.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle matrici](../../javascript/advanced/using-arrays-javascript.md)