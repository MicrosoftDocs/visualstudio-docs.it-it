---
title: Previsto ' @' | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73e7e8fb43bb45e4c97b6bb5ec6c739c16a4423a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349857"
---
# <a name="expected-"></a>Previsto '@'
Si è tentato di creare una variabile da utilizzare con le istruzioni di compilazione condizionale utilizzando il `@set` istruzione, ma non è stato inserito un simbolo di chiocciola "**@**" prima il nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere un simbolo di chiocciola "**@**" immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@set Istruzione](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)