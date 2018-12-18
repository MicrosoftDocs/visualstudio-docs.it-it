---
title: 'CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0b4b154d6e959e636ee75481816a2424d5ea2e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Category|Microsoft. naming|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Una stringa di risorsa contiene una parola composta non sembra essere digitati correttamente.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Ogni parola nella stringa di risorsa è suddivisa in token basati sulle maiuscole e minuscole. Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft. Se riconosciuta, la parola produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, nella regola sono incluse diverse eccezioni e vengono contrassegnate singole parole diverse, ad esempio "Toolbar" e "Nomefile", che deve essere digitati due parole. In questo esempio viene contrassegnato "ToolBar" e "Nomefile".  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare la parola in modo che si è maiuscole e minuscole.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta vengono riconosciute dal dizionario e si desidera utilizzare due parole.  
  
 È anche possibile aggiungere parole composte da un dizionario personalizzato per il correttore ortografico. Parole in un dizionario personalizzato non causano violazioni. Per ulteriori informazioni, vedere [procedura: personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Convenzioni di lettere maiuscole/minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)