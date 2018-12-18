---
title: 'CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f291b603c94292cc86536a212a4ab8286600740b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi
|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Category|Microsoft.Maintainability|
|Modifica importante|Quando viene generato in un parametro che ha lo stesso nome di un campo:<br /><br /> Unificatori - se il campo e il metodo che dichiara il parametro non può essere visualizzate all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Sostanziale - Se si modifica il nome del campo e possono essere visualizzati all'esterno dell'assembly.<br />-Sostanziale - Se si modifica il nome del parametro e il metodo che lo dichiara può essere visualizzato all'esterno dell'assembly.<br /><br /> Quando viene generato su una variabile locale avente lo stesso nome di un campo:<br /><br /> Unificatori - se il campo non può essere visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Unificatori - se si modifica il nome della variabile locale e non modifica il nome del campo.<br />-Sostanziale - Se si modifica il nome del campo e può essere visualizzato all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante. Per intercettare le variabili locali che violano la regola, l'assembly testato deve essere compilato utilizzando le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
 Quando il nome di un campo di istanza corrisponde a un parametro o un nome di variabile locale, il campo di istanza si accede tramite il `this` (`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (parola chiave) all'interno del corpo del metodo. Quando la gestione del codice, è facile dimenticare tale differenza e si presuppone che il parametro o la variabile locale fa riferimento al campo di istanza, con un conseguente errori. Ciò vale soprattutto per i corpi di metodo di lunga durata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare il parametro o una variabile o il campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due violazioni della regola.

 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]