---
title: 'CA1703: Le stringhe di risorsa devono essere digitate correttamente'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22b6dd429c9f2a5e0c3fb1ef3e9e34a7a0fe1a63
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Le stringhe di risorsa devono essere digitate correttamente

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza la stringa di risorsa in parole (suddivisione in token le parole composte) e controlla l'ortografia di ciascuna parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, utilizzare le parole complete che siano state digitate correttamente o aggiungere le parole a un dizionario personalizzato. Per informazioni sull'utilizzo di dizionari personalizzati, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Modificare la lingua di dizionario

Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Se si desidera modificare la lingua del correttore ortografico, è possibile effettuare questa operazione aggiungendo uno dei seguenti attributi per il *AssemblyInfo.cs* oppure *AssemblyInfo. vb* file:

- Utilizzare <xref:System.Reflection.AssemblyCultureAttribute> per specificare le impostazioni cultura, se le risorse si trovano in un assembly satellite.
- Uso <xref:System.Resources.NeutralResourcesLanguageAttribute> per specificare il *lingua* dell'assembly se le risorse sono nello stesso assembly del codice.

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore diverso da delle impostazioni cultura basate su inglese, questa regola di analisi codice invisibile all'utente è disabilitata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Non escludere un avviso da questa regola. Correttamente ortografia consente di ridurre il tempo necessario per l'apprendimento delle nuove librerie di software.

## <a name="related-rules"></a>Regole correlate

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)