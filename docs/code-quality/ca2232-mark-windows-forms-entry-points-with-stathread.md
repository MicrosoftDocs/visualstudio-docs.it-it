---
title: 'CA2232: Punti di ingresso contrassegnare Windows Form con STAThread | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fe12ce5947a22414aaf07c59945fd667b106101f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Fa riferimento a un assembly di <xref:System.Windows.Forms> spazio dei nomi e il relativo punto di ingresso non è contrassegnato con il <xref:System.STAThreadAttribute?displayProperty=fullName> attributo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.STAThreadAttribute>indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione utilizza il modello di apartment a thread multipli, che non è supportato per Windows Form.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]i progetti che usano il Framework dell'applicazione non è necessario contrassegnare il **Main** metodo con STAThread. Il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore esegue automaticamente.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere il <xref:System.STAThreadAttribute> al punto di ingresso dell'attributo. Se il <xref:System.MTAThreadAttribute?displayProperty=fullName> attributo è presente, rimuoverlo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile escludere un avviso da questa regola se sviluppano applicazioni per .NET Compact Framework, per cui il <xref:System.STAThreadAttribute> attributo è necessario e non è supportato.  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti illustrano l'utilizzo corretto di <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]