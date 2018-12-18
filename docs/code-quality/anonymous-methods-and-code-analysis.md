---
title: Metodi anonimi e analisi del codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c7016145d5d34c9077f45f2dbf6c1507aa0e6fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="anonymous-methods-and-code-analysis"></a>Metodi anonimi e analisi del codice
Un *metodo anonimo* è un metodo che non ha nome. Metodi anonimi vengono utilizzati principalmente per passare un blocco di codice come un parametro del delegato.  
  
 Questo argomento illustra la modalità di gestione di avvisi e la metrica che sono associata ai metodi anonimi analisi del codice.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Metodi anonimi dichiarati In un membro  
 Gli avvisi e le metriche per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associate al membro che dichiara il metodo. Non sono associate con il membro che chiama il metodo.  
  
 Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione di **anonymousMethod** deve essere generato in base **Method1** e non **Method2**.  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## <a name="inline-anonymous-methods"></a>Metodi anonimi inline  
 Gli avvisi e le metriche per un metodo anonimo che è dichiarato come un'assegnazione inline a un campo sono associate al costruttore. Se il campo viene dichiarato come `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), avvisi e le metriche vengono associati al costruttore di classe; in caso contrario, sono associate con il costruttore di istanza.  
  
 Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione di **anonymousMethod1** verrà generato in base al costruttore predefinito generato in modo implicito di **classe**. Mentre quelli rilevati **anonymousMethod2** verranno applicate in base al costruttore di classe generato in modo implicito.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Una classe può contenere un metodo anonimo inline che assegna un valore a un campo che contiene più costruttori. In questo caso, gli avvisi e le metriche sono associate a tutti i costruttori, a meno che tale costruttore sia concatenato a un altro costruttore nella stessa classe.  
  
 Ad esempio, nella classe seguente, gli avvisi che si trovano nella dichiarazione di **anonymousMethod** deve essere generato in base **Class (int)** e **Class (String)** ma non in base a **Class ()**.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Anche se ciò potrebbe sembrare imprevisto, questo errore si verifica perché il compilatore genera un metodo univoco per ogni costruttore che non è concatenato a un altro costruttore. A causa di questo comportamento, qualsiasi violazione che si verifica **anonymousMethod** deve essere eliminata separatamente. Ciò significa anche che se è un nuovo costruttore introdotto, gli avvisi che sono stati eliminati in precedenza su **Class (int)** e **Class (String)** devono essere soppressi anche in base al nuovo costruttore.  
  
 È possibile risolvere questo problema in uno dei due modi. È possibile dichiarare **anonymousMethod** in un costruttore comune che concatenati tutti i costruttori. Oppure è possibile dichiararla in un metodo di inizializzazione che viene chiamato da tutti i costruttori.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)