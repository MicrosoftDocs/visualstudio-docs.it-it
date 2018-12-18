---
title: Modelli XSLT predefiniti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe1bf4dda6bed505f0892a18825e93f66e13e16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="xslt-default-templates"></a>Modelli XSLT predefiniti
Se il foglio di stile non contiene corrispondenti regole di modello esplicite, nel corso dell'elaborazione XSLT viene usato un modello predefinito. Il modello predefinito, noto anche come regola di modello incorporata, è definito nella sezione 5.8 della raccomandazione W3C XSLT 1.0 (informazioni in lingua inglese). Il modello predefinito consente al processore XSLT di elaborare un nodo anche in assenza di corrispondenti regole di modello esplicite. Tuttavia, poiché la regola di modello incorporata non è definita in modo esplicito nel foglio di stile, possono verificarsi trasformazioni XSLT impreviste o ambigue.  
  
 Il debugger XSLT visualizza il codice dei modelli XSLT predefiniti. Nel corso di una trasformazione XSLT il modello predefinito eventualmente usato viene visualizzato in una finestra del debugger. Ciò consente di eseguire il codice del modello e di impostare punti di interruzione nelle relative istruzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)