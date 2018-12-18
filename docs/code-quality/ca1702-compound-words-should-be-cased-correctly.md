---
title: 'CA1702: Le parole composte devono essere digitate correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d410f3796cdb30a620f0e0260f8cd529a4428831
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Category|Microsoft. naming|  
|Modifica importante|Interruzione quando viene generato per gli assembly.<br /><br /> Non sostanziale - Quando generato su parametri di tipo.|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore contiene più parole e almeno una delle parole sembra essere una parola composta non è stata definita correttamente.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il nome dell'identificatore è suddiviso in parole che si basano le maiuscole e minuscole. Ogni combinazione di due parole contigui viene controllata dalla libreria del correttore ortografico Microsoft. Se viene riconosciuto, l'identificatore produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, nella regola sono incluse diverse eccezioni e vengono contrassegnate singole parole diverse, ad esempio "Toolbar" e "Nomefile", che devono essere digitati due parole (in questo caso, "ToolBar" e "Nomefile").  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare il nome in modo che si è maiuscole e minuscole.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta vengono riconosciute dal dizionario e si desidera utilizzare due parole.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)   
 [Convenzioni per l'uso di maiuscole e minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)