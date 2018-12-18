---
title: 'CA2228: Non fornire formati di risorse non rilasciati'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1928cb4626ea5d5af15ecf800a8842d66f3e244d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non fornire formati di risorse non rilasciati
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un file di risorse è stato creato utilizzando una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che non è attualmente supportato.

## <a name="rule-description"></a>Descrizione della regola
 File di risorse compilati utilizzando versioni non definitive del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] potrebbe non essere utilizzabili dalle versioni supportate di .NET Framework.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, compilare la risorsa utilizzando una versione supportata del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.