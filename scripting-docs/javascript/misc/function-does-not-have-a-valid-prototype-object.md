---
title: Funzione non dispone di un oggetto prototype valido | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è tentato di utilizzare **instanceof** per determinare se un oggetto derivato da una classe particolare funzione, ma l'oggetto è stata ridefinita `prototype` proprietà come `null`, o un tipo di oggetto esterno (entrambi non valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti). Un oggetto esterno può essere un oggetto del modello di oggetto host (ad esempio, il documento di Internet Explorer o oggetto window) o un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Verificare che la funzione `prototype` proprietà fa riferimento a un oggetto valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)