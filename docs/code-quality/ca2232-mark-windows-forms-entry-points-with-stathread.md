---
title: 'CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 043e1e6de12b3778022d27740793e7426f9eead2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread
|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Fa riferimento a un assembly di <xref:System.Windows.Forms> spazio dei nomi e il relativo punto di ingresso non è contrassegnato con il <xref:System.STAThreadAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.STAThreadAttribute> indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione utilizza il modello di apartment a thread multipli, che non è supportato per Windows Form.

> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i progetti che usano il Framework dell'applicazione non sono necessario contrassegnare il **Main** metodo con STAThread. Il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore esegue automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il <xref:System.STAThreadAttribute> al punto di ingresso dell'attributo. Se il <xref:System.MTAThreadAttribute?displayProperty=fullName> attributo è presente, rimuoverlo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se sviluppano applicazioni per .NET Compact Framework, per cui il <xref:System.STAThreadAttribute> attributo è necessario e non è supportato.

## <a name="example"></a>Esempio
 Gli esempi seguenti illustrano l'utilizzo corretto di <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]