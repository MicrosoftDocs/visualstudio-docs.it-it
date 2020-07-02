---
title: La funzione non ha un oggetto prototipo valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817359"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La funzione non ha un oggetto Prototype valido
Si è provato a usare **instanceof** per determinare se un oggetto è derivato da una classe di funzione particolare, ma è stata ridefinita la proprietà dell'oggetto `prototype` come `null` o un tipo di oggetto esterno (entrambi non [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti validi). Un oggetto esterno può essere un oggetto del modello a oggetti host, ad esempio il documento o l'oggetto finestra di Internet Explorer, oppure un oggetto COM esterno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la proprietà della funzione faccia `prototype` riferimento a un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)