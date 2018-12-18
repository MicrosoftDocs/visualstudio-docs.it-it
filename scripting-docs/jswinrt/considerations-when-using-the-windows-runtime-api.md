---
title: Considerazioni sull'uso dell'API di Windows Runtime | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Considerazioni sull'uso dell'API di Windows Runtime
È possibile usare quasi tutti gli elementi dell'API di Windows Runtime in JavaScript. Tuttavia, esistono alcuni aspetti della rappresentazione JavaScript degli elementi di Windows Runtime che è necessario tenere presenti.  
  
> [!IMPORTANT]
>  Per informazioni sulla creazione di componenti di Windows Runtime in C++, C# o Visual Basic e il loro uso in JavaScript, vedere [Creazione di componenti Windows Runtime in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) e [Creazione di componenti Windows Runtime in C# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Casi speciali nella rappresentazione JavaScript dei tipi di Windows Runtime  
  
-   Stringhe: una stringa non inizializzata è passata a un metodo di Windows Runtime come stringa "non definita" e una stringa impostata su `null` è passata come stringa "null". (Ciò vale ogni volta che un valore `null` o `undefined` viene convertito in una stringa.) Prima di passare una stringa a un metodo di Windows Runtime, è necessario inizializzarla come una stringa vuota ("").  
  
-   Interfacce: non è possibile implementare un'interfaccia di Windows Runtime in JavaScript.  
  
-   Matrici: non è possibile ridimensionare le matrici di Windows Runtime, pertanto i metodi che ridimensionano le matrici in JavaScript non funzionano nelle matrici di Windows Runtime.  
  
-   Matrici: se si passa un valore di matrice JavaScript a un metodo di Windows Runtime, la matrice viene copiata. Il metodo di Windows Runtime non può modificare la matrice o i relativi membri e restituirli all'app di JavaScript. Tuttavia, è possibile usare delle matrici tipizzate (ad esempio, [Oggetto Int32Array](../javascript/reference/int32array-object.md)), che non vengono copiate.  
  
-   Strutture: le strutture di Windows Runtime sono oggetti in JavaScript. Se si desidera passare una struttura di Windows Runtime a un metodo di Windows Runtime, non creare un'istanza della struttura con la parola chiave `new`. In alternativa, creare un oggetto e aggiungere i membri rilevanti e i relativi valori. I nomi dei membri devono essere usati solo con le lettere minuscole: `SomeStruct.firstMember`.  
  
-   Oggetti: gli oggetti JavaScript non sono uguali agli oggetti del codice gestito (`System.Object`). Non è possibile passare un oggetto JavaScript a un metodo di Windows Runtime che richiede un `System.Object`.  
  
-   Identità dell'oggetto: nella maggior parte dei casi, gli oggetti passati avanti e indietro tra JavaScript e Windows Runtime non cambiano. Il motore JavaScript mantiene una mappa di oggetti noti. Quando un oggetto viene restituito da Windows Runtime viene confrontato con la mappa, e se non esiste viene creato un nuovo oggetto. La stessa procedura è seguita per gli oggetti che rappresentano le interfacce che vengono restituite dai metodi di Windows Runtime. Esistono due tipi di eccezioni:  
  
    -   Gli oggetti restituiti da una chiamata di Windows Runtime, e che quindi sono in possesso di nuove proprietà (expando) aggiunte, non mantengono le nuove proprietà quando vengono passate nuovamente a Windows Runtime. Tuttavia, quando vengono restituiti all'app di JavaScript, poiché corrispondono all'oggetto esistente, l'oggetto restituito non è in possesso delle proprietà expando.  
  
    -   Le strutture e i delegati in Windows Runtime non possono essere identificati come identici alle strutture o ai delegati usati in precedenza. Ogni volta che una struttura o un delegato vengono restituiti, ottengono un nuovo riferimento.  
  
-   Conflitti di nome: più interfacce di Windows Runtime possono avere membri con gli stessi nomi. Se vengono combinate in un singolo oggetto JavaScript (che può essere una rappresentazione di una classe di runtime o di un'interfaccia), i membri sono rappresentati con nomi completi. È possibile chiamare questi membri tramite la sintassi seguente: `Class["MemberName"](parameter)`.  
  
     Nel codice seguente, due interfacce dispongono di un metodo Draw, e una classe di runtime implementa entrambe le interfacce.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Ecco come è possibile chiamare il codice sopra riportato in JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out`parametri: se un metodo di Windows Runtime ha più parametri `out`, in JavaScript il metodo è in possesso di un oggetto JavaScript come relativo valore restituito, e l'oggetto è in possesso di proprietà che corrispondono al parametro `out`. Ad esempio, si consideri la firma di Windows Runtime seguente in C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La versione di JavaScript di questa firma è:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     In questo esempio, `returnValue` è un oggetto JavaScript che dispone di due campi: `first` e `second`.  
  
-   I membri statici: Windows Runtime definisce i membri statici e i membri dell'istanza. In JavaScript, i membri statici vengono aggiunti all'oggetto che è associato alla classe o all'interfaccia di Windows Runtime.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Per altre informazioni sulla rappresentazione JavaScript dei tipi di base di Windows Runtime, vedere [Rappresentazione JavaScript dei tipi di Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).