---
title: 'CA2000: Eliminare gli oggetti prima di perdere l''ambito | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 57b499756292a62c64b44f864042ffa740a14016
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Eliminare gli oggetti prima di perdere l'ambito
|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Category|Microsoft.Reliability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un oggetto locale di un <xref:System.IDisposable> tipo viene creato ma l'oggetto non viene eliminato prima di tutti i riferimenti all'oggetto siano esterni all'ambito.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se un oggetto eliminabile non viene eliminato in modo esplicito prima di tutti i relativi riferimenti siano esterni all'ambito, l'oggetto verrà eliminato in un momento indeterminato quando il garbage collector viene eseguito il finalizzatore dell'oggetto. Poiché potrebbe verificarsi un evento eccezionale che impedisca il finalizzatore dell'oggetto di esecuzione, l'oggetto deve essere eliminato in modo esplicito invece.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> per l'oggetto prima di tutti i relativi riferimenti siano esterni all'ambito.  
  
 Si noti che è possibile utilizzare il `using` istruzione (`Using` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) per eseguire il wrapping di oggetti che implementano `IDisposable`. Gli oggetti che vengono inclusi in questo modo verranno automaticamente eliminati alla chiusura del `using` blocco.  
  
 Di seguito sono riportati alcuni casi in cui l'istruzione non è sufficiente per proteggere gli oggetti IDisposable e può causare CA2000 si verifichi.  
  
-   La restituzione di un oggetto eliminabile richiede che l'oggetto viene costruito in un blocco try/finally all'esterno di un utilizzo blocco.  
  
-   L'inizializzazione dei membri di un oggetto eliminabile non deve essere eseguita nel costruttore dell'utilizzo di un'istruzione.  
  
-   Costruttori protetti solo da un gestore di eccezioni di annidamento. Ad esempio,  
  
    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```
  
     causa la generazione di verificarsi a causa di un errore nella costruzione dell'oggetto StreamReader può provocare la chiusura dell'oggetto FileStream CA2000.  
  
-   Oggetti dinamici devono utilizzare un oggetto di ombreggiatura per implementare il modello Dispose degli oggetti IDisposable.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non eliminare un avviso da questa regola a meno che non sia stato chiamato un metodo sull'oggetto che chiama `Dispose`, come <xref:System.IO.Stream.Close%2A>, o se il metodo che ha generato l'avviso restituisce un oggetto IDisposable che fa il wrapping dell'oggetto.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>Esempio  
 Se si implementa un metodo che restituisce un oggetto eliminabile, utilizzare un blocco try/finally senza un blocco catch per assicurarsi che l'oggetto viene eliminato. Tramite un blocco try/finally, si consente a eccezione generato nel punto di errore e verificare che tale oggetto è stato eliminato.  
  
 Nel metodo OpenPort1, la chiamata per aprire l'oggetto ISerializable SerialPort o la chiamata a SomeMethod può non riuscire. In questa implementazione viene generato un avviso di CA2000.  
  
 Nel metodo OpenPort2, due oggetti SerialPort vengono dichiarati e impostato su null:  
  
-   `tempPort`, che consente di verificare l'esito è positivo operazioni del metodo.  
  
-   `port`, che viene utilizzato per il valore restituito del metodo.  
  
 Il `tempPort` viene costruito e aperto in un `try` necessari blocco e qualsiasi altro lavoro viene eseguito nello stesso `try` blocco. Alla fine del `try` blocco, la porta aperta viene assegnato al `port` oggetto che verrà restituito e `tempPort` oggetto è impostato su `null`.  
  
 Il `finally` blocco controlla il valore di `tempPort`. Se non è null, un'operazione nel metodo ha esito negativo, e `tempPort` viene chiuso per assicurarsi che tutte le risorse vengono rilasciate. L'oggetto porta restituito conterrà l'oggetto SerialPort aperto se le operazioni del metodo ha avuto esito positivo o sarà null se l'operazione non riuscita.  

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;
      
   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```
 
## <a name="example"></a>Esempio  
 Per impostazione predefinita, il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore dispone di operatori aritmetici controllo dell'overflow. Pertanto, qualsiasi operazione aritmetica di Visual Basic è potrebbe generare un <xref:System.OverflowException>. Ciò può causare a regole, ad esempio CA2000 violazioni impreviste. Ad esempio, la funzione CreateReader1 seguente produrrà una violazione CA2000 perché il compilatore Visual Basic sta generando un'istruzione per l'aggiunta che potrebbe generare un'eccezione che impedirebbe StreamReader non in fase di eliminazione di controllo dell'overflow.  
  
 Per risolvere questo problema, è possibile disabilitare la creazione di controllo dell'overflow dal compilatore Visual Basic nel progetto oppure è possibile modificare il codice come la funzione CreateReader2 seguente.  
  
 Per disabilitare la creazione di controllo dell'overflow, fare doppio clic sul nome del progetto in Esplora soluzioni e quindi fare clic su **proprietà**. Fare clic su **compilare**, fare clic su **opzioni di compilazione avanzate**e quindi controllare **Rimuovi controllo dell'overflow di integer**.  
  
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Vedere anche  
 <xref:System.IDisposable>   
 [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)