---
title: 'CA1716: Gli identificatori non devono corrispondere a parole chiave'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 079a3502b35807fed39070b59c6ded2e554bf511
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Gli identificatori non devono corrispondere a parole chiave
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un nome di uno spazio dei nomi, un tipo o un membro virtuale o di interfaccia corrisponde a una parola chiave riservata in un linguaggio di programmazione.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per spazi dei nomi, tipi e virtuali e i membri di interfaccia non devono corrispondere a parole chiave definite dai linguaggi con destinazione common language runtime. A seconda del linguaggio utilizzato e la parola chiave, gli errori del compilatore e ambiguità possono rendere difficile da usare la libreria.

 Questa regola confrontato con le parole chiave nelle lingue seguenti:

-   Visual Basic

-   C#

-   C++/CLI

 Viene utilizzato il confronto tra maiuscole e minuscole per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] parole chiave e il confronto tra maiuscole e minuscole viene utilizzato per le altre lingue.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che non compare nell'elenco di parole chiave.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Se si è convinti che l'identificatore verrà confondere gli utenti dell'API, e che la libreria sia utilizzabile in tutte le lingue disponibili in, è possibile eliminare un avviso da questa regola di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].