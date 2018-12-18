---
title: 'CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 977273299e0ae403a3d93501b8879c36096c7c7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione quando viene generato per gli assembly.<br /><br /> Non sostanziale - Quando generato su parametri di tipo.|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene più parole, fra cui almeno una che sembra essere composta e digitata in modo non corretto con distinzione tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola

Il nome dell'identificatore è suddiviso in parole che si basano le maiuscole e minuscole. Ogni combinazione di due parole contigui viene controllata dalla libreria del correttore ortografico Microsoft. Se viene riconosciuto, l'identificatore produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, nella regola sono incluse diverse eccezioni e vengono contrassegnate singole parole diverse, ad esempio "Toolbar" e "Nomefile", che devono essere digitati due parole (in questo caso, "ToolBar" e "Nomefile").

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare il nome in modo che si è maiuscole e minuscole.

## <a name="language"></a>Linguaggio

Il correttore ortografico attualmente controlla solo a dizionari le impostazioni cultura basate su inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto, aggiungendo il **CodeAnalysisCulture** elemento.

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore diverso da delle impostazioni cultura basate su inglese, questa regola di analisi codice invisibile all'utente è disabilitata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta riconosciute dal dizionario e si desidera utilizzare due parole.

## <a name="related-rules"></a>Regole correlate

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche

- [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenzioni per l'uso di maiuscole e minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)