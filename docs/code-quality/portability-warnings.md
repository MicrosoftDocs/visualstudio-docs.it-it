---
title: avvisi di portabilità
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6fe3bcd703d7fd58d5590b755a553d8ead4c0a9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="portability-warnings"></a>avvisi di portabilità
Avvisi di portabilità supportano la portabilità tra diversi sistemi operativi.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola verifica che le strutture dichiarate utilizzando un attributo di un layout esplicito vengano allineate correttamente quando il marshalling a codice non gestito nei sistemi operativi a 64 bit.|
|[CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Questa regola valuta la dimensione di ogni parametro e il valore restituito di P/Invoke e verifica che le dimensioni siano corrette quando il marshalling a codice non gestito nei sistemi operativi a 32 e 64 bit.|
|[CA1903: Usare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|