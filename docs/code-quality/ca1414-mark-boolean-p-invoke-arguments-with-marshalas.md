---
title: 'CA1414: Contrassegnare gli argomenti P-Invoke booleani con MarshalAs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb956c4a5c19441aaa85539909fca3cc7446fd97
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs
|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo di PInvoke dichiarazione include un <xref:System.Boolean?displayProperty=fullName> parametro o valore restituito ma la <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attributo non viene applicato il valore restituito o parametro.

## <a name="rule-description"></a>Descrizione della regola
 Un platform invoke (metodo) accede al codice non gestito e viene definito utilizzando il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Specifica il comportamento di marshalling che viene usato per convertire i tipi di dati tra codice gestito e gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, avere una sola rappresentazione nel codice non gestito e non è necessario specificare il comportamento di marshalling; common language runtime fornisce automaticamente il comportamento corretto.

 Il <xref:System.Boolean> tipo di dati è disponibili più rappresentazioni nel codice non gestito. Quando il <xref:System.Runtime.InteropServices.MarshalAsAttribute> viene omesso, il comportamento di marshalling predefinito di <xref:System.Boolean> è di tipo di dati <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Si tratta di un intero a 32 bit, che non è appropriato in tutte le circostanze. La rappresentazione booleana necessarie per il metodo non gestito deve essere determinata e corrispondere alla appropriata <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool è il tipo BOOL Win32, che è sempre a 4 byte. UnmanagedType. U1 deve essere utilizzata per C++ `bool` o altri tipi di 1 byte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> per il <xref:System.Boolean> parametro o valore restituito. Impostare il valore dell'attributo appropriati <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, è possibile che il codice più facilmente viene mantenuto quando è specificato in modo esplicito il comportamento.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due metodi contrassegnati con l'appropriato PInvoke <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributi.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regole correlate
 [CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)