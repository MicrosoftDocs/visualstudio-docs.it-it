---
title: 'CA1300: Specificare MessageBoxOptions'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2d0b28d804dc6932e66de9dcd758fd05fc888f7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Specificare MessageBoxOptions
|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo chiama l'overload del metodo di <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodo che non accetta un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
 Per visualizzare una finestra di messaggio in modo corretto per le lingue che utilizzano un ordine di lettura da destra a sinistra, il <xref:System.Windows.Forms.MessageBoxOptions> e <xref:System.Windows.Forms.MessageBoxOptions> i membri del <xref:System.Windows.Forms.MessageBoxOptions> enumerazione deve essere passato al <xref:System.Windows.Forms.MessageBox.Show%2A> metodo. Esaminare il <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> proprietà del controllo contenitore per determinare se utilizzare un ordine di lettura da destra a sinistra.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare l'overload del metodo di <xref:System.Windows.Forms.MessageBox.Show%2A> metodo che accetta un <xref:System.Windows.Forms.MessageBoxOptions> argomento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria di codice non verrà localizzata per una lingua che utilizza un ordine di lettura da destra a sinistra.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che visualizza una finestra di messaggio con le opzioni appropriate per l'ordine di lettura delle impostazioni cultura. Un file di risorse, non viene visualizzato, è necessario compilare l'esempio. Seguire i commenti nell'esempio per compilare l'esempio senza un file di risorse e per verificarne la funzionalità da destra a sinistra.

 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Risorse nelle applicazioni Desktop](/dotnet/framework/resources/index)