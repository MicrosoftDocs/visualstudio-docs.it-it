---
title: Risoluzione dei problemi degli script (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-your-scripts-javascript"></a>Risoluzione dei problemi negli script (JavaScript)
In tutti i linguaggi di programmazione possono insorgere situazioni inaspettate. Ad esempio, il valore `null` in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] non si comporta come il valore `Null` nei linguaggi C o C++.  
  
 Ecco alcune delle problematiche che si possono verificare nella generazione di script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax-errors"></a>Errori di sintassi  
 È importante prestare attenzione ai dettagli durante la scrittura di script. Ad esempio, le stringhe devono essere racchiuse tra virgolette.  
  
## <a name="order-of-script-interpretation"></a>Ordine dell'interpretazione degli script  
 L'interpretazione di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fa parte della procedura di analisi HTML del Web Browser. Se in un documento si inserisce uno script nel tag \<HEAD>, questo viene interpretato prima di qualsiasi contenuto del tag \<BODY>. Se vi sono oggetti che vengono creati nel tag \<BODY>, non sono presenti nel momento in cui il tag \<HEAD> viene analizzato e non possono essere modificati dallo script.  
  
> [!NOTE]
>  Questo comportamento è specifico di Internet Explorer. ASP e WSH hanno modelli di esecuzione diversi, come altri host.  
  
## <a name="automatic-type-coercion"></a>Coercizione automatica  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è un linguaggio poco tipizzato con coercizione automatica. Anche se i valori con tipi diversi non sono uguali, le espressioni nell'esempio seguente restituiscono **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Per verificare che il tipo e il valore siano uguali, usare l'operatore di uguaglianza ===. Entrambe le stringhe seguenti restituiscono false:  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Precedenza tra gli operatori  
 La [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md) determina quando viene eseguita un'operazione durante la valutazione di un'espressione. Nell'esempio seguente la moltiplicazione viene eseguita prima della sottrazione, anche se la sottrazione viene prima nell'espressione.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Uso dei cicli for...in con oggetti  
 Quando si scorrono le proprietà di un oggetto con un ciclo [for.... in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), non è possibile prevedere o controllare l'ordine in cui vengono assegnati i campi dell'oggetto alla variabile del contatore di cicli. L'ordine può anche essere diverso nelle diverse implementazioni del linguaggio.  
  
## <a name="with-keyword"></a>Parola chiave with  
 L'istruzione [with](../../javascript/reference/with-statement-javascript.md) risulta utile per l'accesso alle proprietà che già esistono in un oggetto specificato, ma non può essere usata per aggiungere proprietà a un oggetto. Per creare nuove proprietà in un oggetto, è necessario fare riferimento all'oggetto in modo specifico.  
  
## <a name="this-keyword"></a>Parola chiave this  
 Anche se si usa la parola chiave `this` all'interno della definizione di un oggetto per fare riferimento all'oggetto stesso, non è possibile usare `this` o parole chiave simili per fare riferimento alla funzione attualmente in esecuzione quando tale funzione non è una definizione di oggetto. Se la funzione deve essere assegnata a un oggetto come metodo, è possibile usare la parola chiave `this` all'interno della funzione per fare riferimento all'oggetto.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Generazione di uno script che scrive uno script in Internet Explorer  
 Il tag \</SCRIPT> termina lo script corrente se l'interprete lo rileva. Per visualizzare "\</SCRIPT>", riscriverlo su due stringhe almeno, ad esempio "\</SCR" e "IPT>", che è possibile poi concatenare nell'istruzione che le scrive.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Riferimenti a finestra impliciti in Internet Explorer  
 Dal momento che è possibile aprire più di una finestra per volta, tutti i riferimenti a finestra impliciti puntano alla finestra corrente. Per le altre finestre, è necessario usare un riferimento esplicito.