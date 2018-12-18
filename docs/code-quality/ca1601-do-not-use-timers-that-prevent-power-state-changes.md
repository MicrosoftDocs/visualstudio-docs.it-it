---
title: 'CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12e00942bbae9dfdb17f60ec6acac1d18772db3c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza
|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un timer è un intervallo impostato su cui si verificano più di una volta al secondo.

## <a name="rule-description"></a>Descrizione della regola
 Intervallo di polling di una volta al secondo o utilizzare i timer che si verificano più frequentemente una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare gli intervalli di timer in presenti meno di una volta al secondo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola deve essere eliminata solo se è richiesta l'attivazione di più di una volta al secondo il timer e le considerazioni di mobilità possono essere ignorate.