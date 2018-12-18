---
title: "Procedura: valutare un'espressione XPath | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c026e9d2005156189afc9dd478c75397a997d8f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procedura: valutare un'espressione XPath
È possibile valutare le espressioni XPath tramite i **controllo immediato** la finestra di dialogo. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, vale a dire il `self::node()` nodo nel **variabili locali** finestra: fornisce il contesto di valutazione per l'espressione XPath.  
  
 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:  
  
-   Sono supportate le funzioni XPath incorporate.  
  
-   Non sono supportate le funzioni XSLT incorporate.  
  
-   Non sono supportate le funzioni definite dall'utente.  
  
> [!NOTE]
>  La procedura seguente usa i file belowAvg.xsl e books.xml il [procedura dettagliata: Debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) argomento.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Per valutare un'espressione XPath  
  
1.  Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.  
  
2.  Fare clic su di **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
     Il debugger viene avviato e interrotto sul tag `xsl:if`.  
  
3.  Mouse e scegliere **controllo immediato**.  
  
     Il **controllo immediato** viene visualizzata la finestra di dialogo.  
  
4.  Immettere `./price/text()` nel **espressione** campo il **controllo immediato** la finestra di dialogo e fare clic su **Rivaluta**.  
  
     Il prezzo del nodo libro corrente viene visualizzato nel **valore** casella.  
  
5.  Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.  
  
     Il **valore** mostra che l'espressione XPath restituisce `true`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)