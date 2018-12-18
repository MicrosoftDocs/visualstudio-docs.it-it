---
title: Matrice di oggetti (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Oggetto Array (JavaScript)
Fornisce il supporto per la creazione di matrici con qualsiasi tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Array` è assegnato.  
  
 `size`  
 Parametro facoltativo. Dimensione della matrice. Poiché le matrici sono in base zero, gli indici degli elementi creati saranno compresi tra zero e `size` -1.  
  
 `element0,...,elementN`  
 Parametro facoltativo. Elementi da inserire nella matrice. Crea una matrice con  *n*  + 1 elementi e un `length` di  *n*  + 1. Se si usa questa sintassi, è necessario fornire più elementi.  
  
## <a name="remarks"></a>Note  
 Dopo la creazione di una matrice, è possibile accedere ai singoli elementi della matrice usando la notazione [ ]. Si noti che le matrici in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sono in base zero.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 È possibile passare un intero senza segno a 32 bit al costruttore di `Array` per specificare la dimensione della matrice. Se il valore è negativo o non è un intero, verrà generato un errore di run-time. Se si esegue il codice seguente, viene visualizzato questo errore nella console.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Se un singolo valore viene passato al costruttore di `Array` e non è un numero, la proprietà `length` viene impostata su 1 e il valore del solo elemento diventa il singolo argomento passato.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Le matrici JavaScript sono matrici sparse, ossia non tutti gli elementi della matrice possono contenere dati. In JavaScript solo gli elementi che effettivamente contengono dati sono presenti nella matrice. La quantità di memoria usata dalla matrice viene così ridotta.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Alcuni membri dell'elenco seguente sono stati introdotti nelle versioni successive. Per ulteriori informazioni, vedere [informazioni sulla versione](../../javascript/reference/javascript-version-information.md) o la documentazione per i singoli membri.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Array`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-array.md)|Specifica la funzione che crea una matrice.|  
|[Proprietà length (Array)](../../javascript/reference/length-property-array-javascript.md)|Restituisce un valore Integer incrementato di uno rispetto all'elemento massimo definito in una matrice.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-array.md)|Restituisce un riferimento al prototipo per una matrice.|  
  
## <a name="functions"></a>Funzioni  
 La tabella seguente illustra le funzioni dell'oggetto `Array`.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione Array. From](../../javascript/reference/array-from-function-array-javascript.md)|Restituisce una matrice da un oggetto di tipo matrice o iterabile.|  
|[Funzione Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Restituisce un valore booleano che indica se un oggetto è una matrice.|  
|[Funzione Array. of](../../javascript/reference/array-of-function-array-javascript.md)|Restituisce una matrice dagli argomenti passati.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo concat (Array)](../../javascript/reference/concat-method-array-javascript.md)|Restituisce una nuova matrice risultante dalla combinazione di due matrici.|  
|[Metodo Entries](../../javascript/reference/entries-method-array-javascript.md)|Restituisce un iteratore che contiene le coppie chiave/valore della matrice.|  
|[Metodo every](../../javascript/reference/every-method-array-javascript.md)|Controlla se una funzione di callback definita restituisce `true` per tutti gli elementi in una matrice.|  
|[Metodo Fill](../../javascript/reference/fill-method-array-javascript.md)|Popola una matrice con un valore specificato.|  
|[Metodo filter](../../javascript/reference/filter-method-array-javascript.md)|Chiama una funzione di callback definita in ogni elemento di una matrice e restituisce una matrice di valori per i quali la funzione di callback restituisce `true`.|  
|[findIndex (metodo)](../../javascript/reference/findindex-method-array-javascript.md)|Restituisce un valore di indice per il primo elemento della matrice che soddisfa i criteri di test specificati in una funzione di callback.|  
|[Metodo forEach](../../javascript/reference/foreach-method-array-javascript.md)|Chiama una funzione di callback definita per ogni elemento in una matrice.|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md)|Restituisce l'indice della prima occorrenza di un valore in una matrice.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella catena di prototipi di un altro oggetto.|  
|[Metodo join](../../javascript/reference/join-method-array-javascript.md)|Restituisce un oggetto `String` formato da tutti gli elementi concatenati di una matrice.|  
|[Metodo Keys](../../javascript/reference/keys-method-array-javascript.md)|Restituisce un iteratore che contiene le coppie chiave/valore della matrice.|  
|[Metodo lastIndexOf (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|Restituisce l'indice dell'ultima occorrenza di un valore specificato in una matrice.|  
|[Metodo map](../../javascript/reference/map-method-array-javascript.md)|Chiama la funzione di callback specificata in ogni elemento di una matrice e restituisce una matrice contenente i risultati.|  
|[Metodo pop](../../javascript/reference/pop-method-array-javascript.md)|Rimuove l'ultimo elemento di una matrice e lo restituisce.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo push](../../javascript/reference/push-method-array-javascript.md)|Aggiunge nuovi elementi a una matrice e restituisce la nuova lunghezza della matrice.|  
|[Metodo reduce](../../javascript/reference/reduce-method-array-javascript.md)|Accumula un singolo risultato chiamando la funzione di callback definita per tutti gli elementi di una matrice. Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.|  
|[Metodo reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Accumula un singolo risultato chiamando la funzione di callback definita per tutti gli elementi di una matrice, in ordine decrescente. Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.|  
|[Metodo reverse](../../javascript/reference/reverse-method-javascript.md)|Restituisce un oggetto `Array` con gli elementi invertiti.|  
|[Metodo shift](../../javascript/reference/shift-method-array-javascript.md)|Rimuove il primo elemento di una matrice e lo restituisce.|  
|[Metodo slice (Array)](../../javascript/reference/slice-method-array-javascript.md)|Restituisce una sezione di una matrice.|  
|[Metodo some](../../javascript/reference/some-method-array-javascript.md)|Controlla se una funzione di callback definita restituisce `true` per ogni elemento di una matrice.|  
|[Metodo sort](../../javascript/reference/sort-method-array-javascript.md)|Restituisce un oggetto `Array` con gli elementi ordinati.|  
|[Metodo splice](../../javascript/reference/splice-method-array-javascript.md)|Rimuove elementi da una matrice e, se necessario, li sostituisce con nuovi elementi restituendo gli elementi eliminati.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Restituisce una stringa usando le impostazioni locali correnti.|  
|[Metodo toString](../../javascript/reference/tostring-method-array.md)|Restituisce la rappresentazione in formato stringa di una matrice.|  
|[Metodo unshift](../../javascript/reference/unshift-method-array-javascript.md)|Inserisce nuovi elementi all'inizio di una matrice.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-array.md)|Ottiene un riferimento alla matrice.|  
|[Metodo Values](../../javascript/reference/values-method-array-javascript.md)|Restituisce un iteratore che contiene i valori della matrice.|  
  
## <a name="see-also"></a>Vedere anche  
 [App di esempio di scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)