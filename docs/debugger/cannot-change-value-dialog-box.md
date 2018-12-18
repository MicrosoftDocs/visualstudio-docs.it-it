---
title: "Non è possibile modificare la finestra di dialogo valore | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7a6b5cc2c1a5317009225d8e86fd497dc4367787
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="cannot-change-value-dialog-box"></a>Impossibile modificare il valore (finestra di dialogo)
## <a name="error"></a>Error  
 `The value of this variable cannot be changed`&#124; `The name` *nome* `does not exist in the current context` &#124; *vari altri messaggi*  
  
 Questa finestra di messaggio viene visualizzata quando si tenta di modificare il contenuto di una variabile in un valore non consentito in una finestra del debugger (finestre Auto, Espressioni di controllo o Variabili locali) o nella finestra di dialogo Controllo immediato. Se, ad esempio, si tenta di impostare il valore di una variabile Integer in una stringa di caratteri, viene visualizzata questa finestra di messaggio.  
  
## <a name="solution"></a>Soluzione  
 Assicurarsi che l'input digitato nella finestra del debugger o nella finestra di dialogo Controllo immediato rappresenti un valore consentito per la variabile che si sta tentando di impostare.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)