---
title: 'CA1809: Evitare un numero eccessivo di variabili locali'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4790d78ae1050a2c5443a8f048416f5f4de078e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitare un numero eccessivo di variabili locali
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro contiene più di 64 variabili locali, alcune delle quali potrebbe essere generato dal compilatore.

## <a name="rule-description"></a>Descrizione della regola
 Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria, è detto *registrazione* il valore. Common language runtime considera un massimo di 64 variabili locali per la registrazione. Le variabili non registrate vengono inserite nello stack e devono essere spostate in un registro prima della modifica. Per consentire la probabilità che tutte le variabili locali ottenere registrate, limitare il numero di variabili a 64.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, eseguire il refactoring dell'implementazione per utilizzare non più di 64 variabili locali.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sicuro per escludere un avviso da questa regola o disabilitare la regola, se le prestazioni non è un problema.

## <a name="related-rules"></a>Regole correlate
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)