---
title: 'CA1802: Utilizza valori letterali dove appropriato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c2e7841091d3ad5ca093b35b62cca1fdbe6b6a69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizza valori letterali dove appropriato
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Category|Microsoft. Performance|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un campo viene dichiarato `static` e `readonly` (`Shared` e `ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzato con un valore calcolabile in fase di compilazione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il valore di un `static``readonly` campo viene calcolato in fase di esecuzione quando viene chiamato il costruttore statico per il tipo dichiarante. Se il `static``readonly` campo viene inizializzato quando viene dichiarata e un costruttore statico non è dichiarato in modo esplicito, il compilatore genera un costruttore per inizializzare il campo statico.  
  
 Il valore di un `const` campo viene calcolato in fase di compilazione e archiviato nei metadati, aumentando le prestazioni di runtime quando viene confrontata con un `static``readonly` campo.  
  
 Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un `const` in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il `static` e `readonly` modificatori con il `const` modificatore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile escludere un avviso da questa regola o disabilitare la regola, se le prestazioni non è un problema.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo, `UseReadOnly`, che viola la regola e un tipo, `UseConstant`, che soddisfa la regola.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]