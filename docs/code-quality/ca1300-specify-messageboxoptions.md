---
title: 'CA1300: Specificare MessageBoxOptions | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b47c5f2297d9b13e33dc064a203bfd84ce2d196f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)