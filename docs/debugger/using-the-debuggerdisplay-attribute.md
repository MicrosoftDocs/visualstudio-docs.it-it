---
title: Utilizzo dell'attributo DebuggerDisplay | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 11770efcc517b9ec713656f540d75b0a2c412ae7
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="using-the-debuggerdisplay-attribute"></a>Utilizzo dell'attributo DebuggerDisplay
Il [DebuggerDisplayAttribute (classe)](/dotnet/api/system.diagnostics.debuggerdisplayattribute) controlla come un oggetto, una proprietà o un campo nelle finestre delle variabili del debugger. Questo attributo può essere applicato a tipi, delegati, proprietà, campi e assembly.  
  
 L'attributo `DebuggerDisplay` presenta un solo argomento, costituito da una stringa da visualizzare nella colonna del valore per le istanze del tipo. Questa stringa può contenere parentesi graffe (`{` e `}`). Il testo racchiuso tra due parentesi graffe viene valutato come un campo, una proprietà o un metodo.  
  
 Se una classe dispone di un metodo `ToString()` sottoposto a override, il debugger usa il metodo sottoposto a override anziché il valore `{<typeName>}`predefinito. Pertanto, se è stato eseguito l'override del metodo `ToString()` , il debugger usa il metodo sottoposto a override anziché il valore`{<typeName>}`predefinito e non è necessario usare `DebuggerDisplay`. Se si usano entrambi, l'attributo `DebuggerDisplay` avrà la precedenza sul metodo `ToString()` sottoposto a override.  
  
 La valutazione da parte del debugger di questa chiamata implicita a `ToString()` dipende da un'impostazione utente nella finestra di dialogo **Strumenti / Opzioni / Debug** . In Visual Basic questa valutazione implicita di `ToString()` non è implementata.  
  
> [!IMPORTANT]
>  Se la casella di controllo **Mostra struttura non elaborata degli oggetti nelle finestre delle variabili** è selezionata nella finestra di dialogo **Strumenti / Opzioni / Debug** , l'attributo `DebuggerDisplay` viene ignorato.  
  
 Nella tabella riportata di seguito vengono visualizzati alcuni utilizzi possibili dell'attributo `DebuggerDisplay` e alcuni output di esempio.  
  
|Attributo|Output visualizzato nella colonna valore|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Utilizzato in un tipo con campi `x` e `y`.|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`La sintassi del parametro può variare a seconda del linguaggio. Prestare, pertanto, particolare attenzione.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` può anche accettare parametri denominati.  
  
|Parametri|Scopo|  
|----------------|-------------|  
|`Name`, `Type`|Questi parametri influiscono sulle colonne **Nome** e **Tipo** delle finestre delle variabili. Possono essere impostati su stringhe utilizzando la stessa sintassi del costruttore. L'utilizzo eccessivo o errato di questi parametri può generare output poco chiaro.|  
|`Target`, `TargetTypeName`|Specifica il tipo di destinazione quando l'attributo viene utilizzato a livello di assembly.|  
  
 Il file autoexp.cs usa l'attributo DebuggerDisplay a livello di assembly. Il file autoexp.cs determina le espansioni predefinite usate da Visual Studio per gli oggetti .NET. Esaminare il file autoexp.cs per esempi di utilizzo dell'attributo DebuggerDisplay oppure modificare e compilare il file autoexp.cs per modificare le espansioni predefinite. Assicurarsi di eseguire il backup del file autoexp.cs prima di modificarlo.  
  
 Per compilare autoexp.cs, aprire un prompt dei comandi per gli sviluppatori per VS2015 ed eseguire i comandi seguenti.  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Le modifiche apportate ad autoexp.dll verranno rilevate nella sessione di debug successiva.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Utilizzo di espressioni in DebuggerDisplay  
 Sebbene sia possibile utilizzare un'espressione generale tra parentesi graffe in un attributo DebuggerDisplay, questa procedura non è consigliata.  
  
 Un'espressione generale in DebuggerDisplay ha accesso implicito al puntatore `this` solo per l'istanza corrente del tipo di destinazione. L'espressione non ha accesso ad alias, variabili locali o puntatori. Se l'espressione fa riferimento a delle proprietà, gli attributi su tali proprietà non vengono elaborati. Ad esempio, il codice c# `[DebuggerDisplay("Object {count - 2}")]` Visualizza `Object 6` se il campo `count` è 8.  
  
 L'utilizzo di espressioni in DebuggerDisplay può causare i problemi seguenti:  
  
-   La valutazione delle espressioni è l'operazione più dispendiosa nel debugger e viene valutata ogni volta che viene visualizzata. Ciò può causare problemi relativi alle prestazioni nell'esecuzione del codice istruzione per istruzione. Ad esempio, un'espressione complessa che viene utilizzata per visualizzare i valori in una raccolta o in un elenco può essere molto lenta quando è presente un grande numero di elementi.  
  
-   Le espressioni vengono valutate dall'analizzatore di espressioni del linguaggio dello stack frame corrente, non dall'analizzatore del linguaggio in cui l'espressione è stata scritta. Questa situazione può provocare risultati imprevisti quando i linguaggi sono diversi.  
  
-   La valutazione di un'espressione può modificare lo stato dell'applicazione. Ad esempio, un'espressione che imposta il valore di una proprietà modifica il valore della proprietà nel codice in esecuzione.  
  
 Per ridurre i possibili problemi della valutazione dell'espressione, è possibile creare una proprietà privata che esegue l'operazione e restituisce una stringa. L'attributo DebuggerDisplay può quindi visualizzare il valore di tale proprietà privata. Nell'esempio seguente viene implementato questo modello:  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato l'utilizzo di `DebuggerDisplay`, insieme a `DebuggerBrowseable` e `DebuggerTypeProxy`. Quando è visualizzato in una finestra delle variabili del debugger, come la finestra **Espressioni di controllo** , produce un'espansione analoga alla seguente:  
  
|**Name**|**Valore**|**Type**|  
|--------------|---------------|--------------|  
|Chiave|"three"|oggetto {string}|  
|Valore|3|oggetto {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }
    
    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Creare viste personalizzate di oggetti gestiti](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Identificatori di formato in c#](../debugger/format-specifiers-in-csharp.md)   
 [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
