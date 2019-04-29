---
title: Previsto oggetto Regular expression | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a42cf4b76f4de6d4170f7ef85dafc00841964cfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006421"
---
# <a name="regular-expression-object-expected"></a>Previsto un oggetto di espressione regolare
Si è provato a richiamare il **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodo in un oggetto di un tipo diverso da `RegExp`. L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Richiamare solo le **RegExp.prototype.toString** oppure **RegExp.prototype.valueOf** metodi su oggetti di tipo `RegExp`.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)