---
title: L'URI da codificare contiene un carattere non valido | Documenti Microsoft
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI da codificare contiene un carattere non valido
Si è tentato di codificare una stringa come un URI (Uniform Resource Identifier), ma contiene caratteri non validi. Sebbene la maggior parte dei caratteri sono validi all'interno di stringhe da convertire in URI, alcune sequenze di caratteri Unicode non sono valide.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare la stringa da codificare contiene solo le sequenze Unicode valide. Un URI completo è costituito da una sequenza di componenti e separatori. I nomi delle parentesi angolari rappresentano i componenti e il ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori. Il formato generale è:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)