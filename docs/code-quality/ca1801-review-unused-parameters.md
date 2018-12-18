---
title: 'CA1801: Rivedere i parametri inutilizzati'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aae1661d848e2b7a49dc1873dbe1f555bef6abc0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Rivedere i parametri inutilizzati
|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Category|Microsoft.Usage|
|Modifica importante|Non sostanziale - Se il membro non è visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br /><br /> Non sostanziale - Se si modifica il membro per usare il parametro all'interno del corpo.<br /><br /> Sostanziale - Se si rimuove il parametro e è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Una firma di metodo include un parametro non utilizzato nel corpo del metodo. Questa regola esamina i metodi seguenti:

-   Metodi a cui fa riferimento un delegato.

-   Metodi usati come gestori eventi.

-   I metodi dichiarati con la `abstract` (`MustOverride` in Visual Basic) modificatore.

-   I metodi dichiarati con la `virtual` (`Overridable` in Visual Basic) modificatore.

-   I metodi dichiarati con la `override` (`Overrides` in Visual Basic) modificatore.

-   I metodi dichiarati con la `extern` (`Declare` istruzione in Visual Basic) modificatore.

## <a name="rule-description"></a>Descrizione della regola
 Rivedere i parametri dei metodi non virtuali che non vengono utilizzati nel corpo del metodo per non verificare che nessun correttezza esiste nell'errore di accesso. I parametri inutilizzati comportano costi di manutenzione e prestazioni.

 Talvolta una violazione di questa regola può puntare a un bug di implementazione del metodo. Ad esempio, il parametro deve essere utilizzato nel corpo del metodo. Esclusione di avvisi di questa regola se il parametro deve essere presente per la compatibilità con le versioni precedenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il parametro non utilizzato (una modifica di rilievo) o usare il parametro nel corpo del metodo (una modifica non sostanziale).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola per il codice fornito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due metodi. Un metodo viola la regola e l'altro metodo soddisfa la regola.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)