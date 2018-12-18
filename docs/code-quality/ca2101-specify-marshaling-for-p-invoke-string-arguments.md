---
title: 'CA2101: Specificare il marshalling per gli argomenti di stringa P-Invoke | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 15191983d08bfc99848e4a16c0059c075b234bb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Category|Microsoft.Globalization|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Platform invoke membro consente chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling della stringa.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando si converte da Unicode ad ANSI, è possibile che non tutti i caratteri Unicode possono essere rappresentati in una tabella codici ANSI specifica. *Il mapping più appropriato* tenta di risolvere il problema tramite la sostituzione di un carattere per il carattere che non può essere rappresentato. L'utilizzo di questa funzionalità può causare una potenziale vulnerabilità di sicurezza, perché non è possibile controllare il carattere che viene scelto. Ad esempio, il codice dannoso potrebbe intenzionalmente creare una stringa Unicode che contiene caratteri che non si trovano in una particolare tabella codici, che vengono convertiti in caratteri speciali del file system, ad esempio '... ' o '/'. Si noti inoltre che i controlli di sicurezza per i caratteri speciali vengono frequentemente eseguiti prima che la stringa viene convertita in formato ANSI.  
  
 Il mapping più appropriato è il valore predefinito per la conversione non gestita, WChar a MByte. A meno che non si disabilita in modo esplicito il mapping più appropriato, il codice potrebbe contenere una vulnerabilità della protezione a causa di questo problema.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire il marshalling esplicito i tipi di dati stringa.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che viola la regola e quindi viene illustrato come correggere la violazione.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]