---
title: DA0011-CompareTo costoso | Microsoft Docs
description: Il metodo CompareTo del tipo è dispendioso o alloca memoria.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91219bed2ca0e8b4bbc28825e1505b9d5f78bbc8
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466154"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Funzione CompareTo dispendiosa

|Elemento|valore|
|-|-|
|ID regola|DA0011|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento<br /><br /> Memoria .NET|
|Message|Le funzioni CompareTo dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione CompareTo.|
|Tipo regola|Avviso|

## <a name="cause"></a>Causa
 Il metodo CompareTo del tipo è dispendioso o alloca memoria.

## <a name="rule-description"></a>Descrizione della regola
 I metodi CompareTo dovrebbero essere efficienti e non allocare memoria.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Ridurre la complessità del metodo CompareTo.
