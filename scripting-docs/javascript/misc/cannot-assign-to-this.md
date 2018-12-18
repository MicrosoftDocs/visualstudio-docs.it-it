---
title: "Non è possibile assegnare a &#39; questo &#39; | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>Non è possibile assegnare a &#39; questo &#39;
Si è tentato di assegnare un valore a **questo**. **questo** è un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] (parola chiave) che fa riferimento a uno:  
  
-   l'oggetto attualmente in esecuzione un metodo,  
  
-   l'oggetto globale, se nessun metodo corrente (o il metodo non appartiene a un altro oggetto).  
  
 Un metodo è un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzione che viene richiamato tramite un oggetto. All'interno di un metodo di **questo** (parola chiave) è un riferimento all'oggetto tramite cui è stato richiamato il metodo (situazione che si verifica all'oggetto creato richiamando il costruttore della classe con il **nuova** operatore).  
  
 All'interno di un metodo, è possibile utilizzare **questo** per fare riferimento all'oggetto corrente, ma non è possibile assegnare un nuovo valore per **questo**.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Non tentare di assegnare a **questo**. Per accedere a una proprietà o metodo di un oggetto istanza, utilizzare l'operatore punto (ad esempio, un cerchio**.** raggio).  
  
    > [!NOTE]
    >  È possibile assegnare il nome variabile creata dall'utente **questo**; è un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] parola riservata.  
  
## <a name="see-also"></a>Vedere anche  
 [Questa istruzione](../../javascript/reference/this-statement-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)