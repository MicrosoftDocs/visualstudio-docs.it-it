---
title: 'CA1822: Contrassegna i membri come statici'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19ca5639b72462f49a818b50a9aaae6e795342b9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici
|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale - Se il membro non è visibile all'esterno dell'assembly, indipendentemente dal fatto le modifiche apportate. Non sostanziale - Se si modifica solo il membro a un membro di istanza con il `this` (parola chiave).<br /><br /> Sostanziale - Se si modifica il membro da un membro di istanza a un membro statico e è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un membro che non accedono ai dati di istanza non è contrassegnato come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descrizione della regola
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Per evitare un controllo in fase di esecuzione per ogni chiamata che consente di verifica che il puntatore all'oggetto corrente è diverso da null, la creazione di siti di chiamata non virtuali. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili delle prestazioni. In alcuni casi, l'errore per accedere all'istanza di oggetto corrente rappresenta un problema di correzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Contrassegnare il membro come static (o condivise in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o utilizzare 'this' / 'Me' nel metodo corpo, se appropriato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola per il codice fornito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)