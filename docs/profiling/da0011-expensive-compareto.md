---
title: 'DA0011: Funzione CompareTo dispendiosa | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f7ef867fc40a93948e4de4f5410609ef03aff19
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="da0011-expensive-compareto"></a>DA0011: Funzione compareTo dispendiosa
|||  
|-|-|  
|ID regola|DA0011|  
|Category|Uso di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Memoria .NET|  
|Messaggio|Le funzioni CompareTo dovrebbero essere semplici e non allocare memoria. Se possibile, ridurre la complessità della funzione CompareTo.|  
|Tipo regola|Avviso|  
  
## <a name="cause"></a>Causa  
 Il metodo CompareTo del tipo è dispendioso o alloca memoria.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi CompareTo dovrebbero essere efficienti e non allocare memoria.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ridurre la complessità del metodo CompareTo.