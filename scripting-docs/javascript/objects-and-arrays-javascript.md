---
title: Oggetti e matrici (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objects-and-arrays-javascript"></a>Oggetti e matrici (JavaScript)
Gli oggetti [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono costituiti da una raccolta di proprietà e metodi. Un metodo è una funzione membro di un oggetto. Una proprietà è un valore o un insieme di valori (sotto forma di matrice od oggetto) membro di un oggetto. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] supporta quattro tipi di oggetti:  
  
-   Oggetti intrinseci, ad esempio `Array` e `String`.  
  
-   Oggetti creati.  
  
-   Oggetti host, ad esempio `window` e `document`.  
  
-   Oggetti ActiveX  
  
## <a name="expando-properties-and-methods"></a>Proprietà e metodi Expando  
 Tutti gli oggetti in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] supportano proprietà e metodi expando o proprietà che possono essere aggiunte e rimosse in fase di esecuzione. Queste proprietà e questi metodi possono avere qualsiasi nome ed essere identificati da numeri. Se il nome della proprietà o del metodo è un semplice identificatore, potrà essere scritto dopo il nome dell'oggetto seguito da un punto, ad esempio `myObj.name`, `myObj.age` e `myObj.getAge` nel codice riportato di seguito:  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Se il nome della proprietà o del metodo non è un semplice identificatore o è sconosciuto nel momento di scrittura dello script, è possibile utilizzare un'espressione tra parentesi quadre per indicizzare la proprietà. I nomi di tutte le proprietà expando in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] vengono convertiti in stringhe prima di essere aggiunti all'oggetto.  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Per informazioni sulla creazione di un oggetto da una definizione, vedere [Creazione di oggetti](../javascript/creating-objects-javascript.md).  
  
## <a name="arrays-as-objects"></a>Matrici come oggetti  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], gli oggetti e le matrici sono gestiti in modo quasi identico, poiché le matrici sono solo un particolare tipo di oggetto. Sia gli oggetti che le matrici possono disporre di proprietà e metodi.  
  
 Le matrici hanno una proprietà `length`, mentre gli oggetti no. Quando si assegna un valore a un elemento di una matrice il cui indice è superiore alla sua lunghezza (ad esempio `myArray[100] = "hello"`), la proprietà `length` viene automaticamente aumentata fino alla nuova lunghezza. Analogamente, se si rende la proprietà `length` più piccola, qualsiasi elemento il cui indice è al di fuori della lunghezza della matrice viene eliminato.  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Le matrici forniscono metodi per scorrere e modificare i membri. Nell'esempio seguente viene illustrato come ottenere le proprietà di oggetti archiviati in una matrice.  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>Matrici multidimensionali  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] non supporta direttamente le matrici multidimensionali, ma è possibile ottenere il comportamento delle matrici multidimensionali archiviando le matrici all'interno di un'altra matrice. È possibile memorizzare qualsiasi tipo di dati degli elementi di matrice, comprese altre matrici. Ad esempio, il codice seguente consente di compilare una tavola pitagorica per i numeri fino a 5.  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```