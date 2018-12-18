---
title: Visualizzazione di testo in una pagina Web (JavaScript) | Microsoft Docs
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
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="displaying-text-in-a-webpage-javascript"></a>Visualizzazione di testo in una pagina Web (JavaScript)
Esistono diversi modi per visualizzare testo in una pagina Web. Ognuno presenta vantaggi e svantaggi e supporta utilizzi specifici.  
  
## <a name="displaying-text"></a>Visualizzazione di testo  
  
-   La modalità consigliata per visualizzare testo è quella di creare un elemento e di scrivere nella proprietà textContent.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     In questo esempio, il valore di `text` è "my text". Tuttavia, il valore derivante dal recupero o dall'impostazione della proprietà `textContent` su un nodo padre potrebbe includere il contenuto di testo dei figli del nodo. Nell'esempio seguente viene mostrato che il `textContent` impostato su un nodo figlio viene incluso nel valore del `textContent` del nodo padre:  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     In questo esempio, il valore di `text` è "[nested]".  
  
-   È inoltre possibile creare un elemento e scrivere nelle proprietà [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) o [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx). L'impostazione di queste proprietà influisce solo sul testo nell'elemento stesso, non nei relativi elementi figlio. Tuttavia, queste proprietà presentano anche alcuni svantaggi:  
  
    -   La proprietà [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) non funziona in tutti i browser, pertanto è consigliabile evitarla per motivi di compatibilità.  
  
    -   La proprietà [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) è influenzata dagli stili CSS e non viene visualizzata se l'elemento è nascosto.  
  
    -   La proprietà [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) ottiene e imposta sia i nodi annidati che il testo. Se non è protetta, potrebbe essere usata per attacchi script injection. Inoltre, l'impostazione su testo senza tag HTML rimuove tutti i nodi precedentemente impostati.  
  
-   È possibile utilizzare il metodo `document.write` senza dover creare un elemento. Tuttavia, l'utilizzo di questo metodo fa si che l'intera pagina Web venga cancellata, risultato che potrebbe non corrispondere a quello desiderato.  
  
     Nell'esempio seguente viene illustrato uno degli svantaggi dell'utilizzo di `document.write`. Lo script è progettato per visualizzare l'ora ogni 5 secondi, ma la mostra solo due volte. Prima che venga chiamato `document.write` per la seconda volta, il caricamento della pagina sarà stato completato e `document.write` quindi rimuove l'intera pagina (chiama `document.open`). A questo punto, la funzione `ShowTime` non esiste più.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Per correggere il codice precedente, rimuovere la riga di codice che contiene `document.write` e rimuovere il commento dalle due righe di codice seguenti impostate come commento.  
  
-   È anche possibile usare `alert``prompt`, o la funzione `confirm` che visualizza un messaggio in una finestra popup. Nella maggior parte dei casi non è consigliabile usare una finestra popup in un Web browser. La maggior parte dei browser moderni ha impostazioni che bloccano automaticamente le finestre popup, perciò il messaggio potrebbe non essere visualizzato. Inoltre, è possibile entrare in un ciclo infinito quando si utilizzano le finestre popup, rendendo impossibile all'utente la chiusura della pagina Web nel modo abituale.