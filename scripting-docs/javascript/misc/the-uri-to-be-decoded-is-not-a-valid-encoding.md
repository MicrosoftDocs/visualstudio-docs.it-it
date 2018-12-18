---
title: "L'URI da decodificare è non una codifica valida | Documenti Microsoft"
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>La codifica usata per l'URI da decodificare non è valida
Si è tentato di decodificare un formato non corretto URI (Uniform Resource Identifier). Gli URI hanno una sintassi speciale. la maggior parte dei caratteri non alfanumerici devono essere codificati prima di poter essere usati in un URI. È possibile utilizzare il `encodeURI` e `encodeURIComponent` metodi per creare un URI da una normale [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringa.  
  
 Un URI completo è costituito da una sequenza di componenti e separatori. Il formato generale è:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 I nomi delle parentesi angolari rappresentano i componenti e il ":", "/", ";" e "?" sono caratteri riservati utilizzati come separatori.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che si sta tentando di decodificare solo URI validi. Impossibile decodificare normale [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] stringhe, poiché potrebbero contenere caratteri non validi.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)