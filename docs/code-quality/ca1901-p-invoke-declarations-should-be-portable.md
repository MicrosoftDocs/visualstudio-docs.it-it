---
title: 'CA1901: le Dichiarazioni P-Invoke devono essere portabili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6e0d3ce3d0130b0a2cf40f6d4f1716c32ae7c40e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Le dichiarazioni P/Invoke devono essere portabili
|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Category|Microsoft.Portability|  
|Modifica importante|Sostanziale - P/Invoke è visibile all'esterno dell'assembly. Non sostanziale - Se P/Invoke non è visibile all'esterno dell'assembly.|  
  
## <a name="cause"></a>Causa  
 La regola valuta la dimensione di ogni parametro e il valore restituito di P/Invoke e verifica che la dimensione del marshalling a codice non gestito in piattaforme a 32 bit e 64 bit, sia corretta. La violazione di questa regola più comune consiste nel passare un integer a dimensione fissa in cui è necessaria una variabile dipendente dalla piattaforma, della dimensione del puntatore.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Uno dei seguenti scenari viola questa regola si verifica:  
  
-   Il valore restituito o parametro è tipizzato come intero a dimensione fissa quando deve essere digitato come un `IntPtr`.  
  
-   Il valore restituito o parametro è tipizzato come un `IntPtr` quando deve essere digitato come numero intero di dimensioni fisse.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 È possibile correggere la violazione utilizzando `IntPtr` o `UIntPtr` per rappresentare gli handle anziché `Int32` o `UInt32`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non è necessario eliminare l'avviso.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra una violazione di questa regola.  
  
```csharp  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 In questo esempio, il `nIconIndex` parametro è dichiarato come un `IntPtr`, che è di 4 byte su una piattaforma a 32 bit e 8 byte su una piattaforma a 64 bit. Nella dichiarazione di non gestita che segue, è possibile vedere che `nIconIndex` è un intero senza segno a 4 byte in tutte le piattaforme.  
  
```csharp  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## <a name="example"></a>Esempio  
 Per correggere la violazione, modificare la dichiarazione per le operazioni seguenti:  
  
```csharp  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Portability Warnings](../code-quality/portability-warnings.md)