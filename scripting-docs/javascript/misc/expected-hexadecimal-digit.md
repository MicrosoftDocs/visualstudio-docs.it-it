---
title: Prevista cifra esadecimale | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="expected-hexadecimal-digit"></a>Prevista cifra esadecimale
Creazione di una sequenza di escape Unicode non corretta. Le sequenze di escape Unicode iniziano con \u, seguito da quattro cifre esadecimali (non sono più presenti e non meno). Cifre esadecimali Unicode possono contenere solo i numeri 0-9, lettere maiuscole A-F e le lettere minuscole-f. L'esempio seguente illustra una sequenza di escape Unicode corretta.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che le cifre esadecimali Unicode iniziano con \u, contiene solo i numeri 0-9, lettere maiuscole A-F, lettere minuscole lettere a-f; e vengono raggruppati in quattro cifre.  
  
    > [!NOTE]
    >  Se si desidera utilizzare il testo letterale \u in una stringa, quindi utilizzare due barre rovesciate - (\\\u)-uno per la prima barra rovesciata di escape.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati](../../javascript/data-types-javascript.md)