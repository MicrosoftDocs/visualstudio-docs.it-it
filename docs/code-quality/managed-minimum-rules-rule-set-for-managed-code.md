---
title: Set di regole minime gestite per codice gestito
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 95264aafd2467065ee2bc36d463369f19714dd68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587355"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Set di regole minime gestite per codice gestito

Le regole minime gestite sono incentrate sui problemi più critici del codice, inclusi i potenziali problemi di sicurezza, gli arresti anomali dell'applicazione e altri importanti errori di logica e progettazione. Includere questo set di regole in tutti i set di regole personalizzati creati per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1821](../code-quality/ca1821.md)|Rimuovere i finalizzatori vuoti|
|[CA2213](../code-quality/ca2213.md)|I campi eliminabili devono essere eliminati|
|[CA2231](../code-quality/ca2231.md)|Operatore di overload uguale a in sostituzione di `ValueType.Equals`|
