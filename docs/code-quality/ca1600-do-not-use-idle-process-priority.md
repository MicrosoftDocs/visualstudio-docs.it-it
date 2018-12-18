---
title: ": Non CA1600 processo inattivo priorità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Category|Microsoft.Mobility|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Non impostare la priorità del processo su Inattivo. I processi con `System.Diagnostics.ProcessPriorityClass.Idle` . Idle occupano la CPU diversamente sarebbe inattiva e blocca quindi la modalità standby.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Impostare i processi su `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Questa regola deve essere eliminata solo quando è necessaria una priorità di processo su inattivo e le considerazioni sulla mobilità possono essere ignorati.