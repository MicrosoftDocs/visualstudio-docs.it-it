---
title: 'CA2204: I valori letterali devono essere digitati correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: I valori letterali devono essere digitati in modo corretto
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un metodo passa una stringa letterale che viene utilizzata in un parametro o una proprietà che richiede una stringa localizzata e la stringa letterale contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola consente di controllare una stringa letterale che viene passata come un valore per un parametro o una proprietà quando uno o più delle seguenti condizioni sono true:  
  
-   Il <xref:System.ComponentModel.LocalizableAttribute> attributo di parametro o la proprietà è impostata su true.  
  
-   Il nome di parametro o la proprietà contiene "Text", "Messaggio" o "Didascalia".  
  
-   Il nome del parametro di stringa che viene passato a un metodo Write o console. WriteLine è "value" o "format".  
  
 Questa regola analizza la stringa letterale in parole, suddivisione in token le parole composte e controlla l'ortografia di ciascuna parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola al dizionario personalizzato. Per informazioni sull'utilizzo di dizionari personalizzati, vedere [procedura: personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Correttamente ortografia consente di ridurre la curva di apprendimento necessaria per le nuove librerie software.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)