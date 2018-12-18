---
title: 'Debug di F # | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b3bb2a9379dd6cd43bb0398ccda2b031b96d56e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-f"></a>Debug di F#
Il debug di F #è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:  
  
-   Il **Auto** non vengono visualizzate le variabili F #.  
  
-   La modifica e la continuazione non sono supportate per F#. La modifica del codice F# durante una sessione di debug è possibile ma deve essere evitata. Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.  
  
-   Il debugger non riconosce le espressioni F#. Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F#, è necessario tradurre l'espressione nella sintassi C#. Quando si traduce un'espressione F# in C#, ricordare che C# utilizza == come operatore di confronto per uguaglianza e che F# utilizza un solo =.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
