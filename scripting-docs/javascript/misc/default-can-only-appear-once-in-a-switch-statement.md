---
title: "'default' può apparire solo una volta in un'istruzione 'switch' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5d31a74900e8eee5daa97bb7f9af5146b237e04
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842182"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' può apparire una sola volta in un'istruzione 'switch'
Si è provato a usare il **predefinito** istruzione più volte all'interno di un'istruzione switch. Nel caso predefinito è sempre l'ultima istruzione case in un'istruzione switch (è il caso di FallThrough).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Rimuovere qualsiasi elemento aggiuntivo **predefinito** caso le istruzioni dal `switch` istruzione (usare la maggior parte delle istruzione case a un valore predefinito nell'istruzione switch).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Parole riservate in JavaScript](../../javascript/reference/javascript-reserved-words.md)