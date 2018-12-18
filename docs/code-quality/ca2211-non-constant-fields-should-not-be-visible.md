---
title: 'CA2211: I campi non costanti non devono essere visibili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c36de9e19f01bad47bba390975d5ab59f2fd6e5c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: I campi non costanti non devono essere visibili
|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo statico pubblico o protetto non è costante, non è in sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 I campi statici che non sono costanti né in sola lettura non sono thread-safe. Accesso a tali campi deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe. Poiché si tratta di competenze di difficile informazioni e master e un oggetto di questo test presenta difficoltà, i campi statici sono più utilizzati per archiviare i dati che non cambiano. Questa regola si applica a librerie. le applicazioni non devono esporre tutti i campi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere il campo statico costante o di sola lettura. In caso contrario, è possibile riprogettare il tipo per utilizzare un meccanismo alternativo, ad esempio una proprietà di thread-safe che gestisce l'accesso thread-safe per il campo sottostante. Tenere presente che problemi di contesa dei blocchi e i deadlock possono influire sulle prestazioni e il comportamento della libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se si sviluppa un'applicazione e pertanto avere il pieno controllo sull'accesso al tipo che contiene il campo statico. Progettazione delle librerie di non escludere un avviso da questa regola. utilizzo di campi statici non costante può rendere utilizza la libreria difficile per gli sviluppatori per usare correttamente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]