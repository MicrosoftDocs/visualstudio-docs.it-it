---
title: "Proprietà dei dati e delle funzioni di accesso | Microsoft Docs"
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>Proprietà dei dati e proprietà delle funzioni di accesso
Questa sezione include tutte le informazioni utili relative alle proprietà dei dati e alle proprietà della funzione di accesso.  
  
### <a name="data-properties"></a>Proprietà dei dati  
 Un oggetto *proprietà dei dati* è una proprietà che può ottenere e impostare un valore. Le proprietà dei dati contengono le proprietà `value` e `writable` nei loro descrittori.  
  
 Nella tabella seguente sono elencati gli attributi per un descrittore di proprietà dei dati.  
  
|Attributo del descrittore dei dati|Descrizione|Impostazione predefinita|  
|-------------------------------|-----------------|-------------|  
|`value`|Valore corrente della proprietà.|`undefined`|  
|`writable`|`true` o `false`. Se `writable` è impostato su `true`, il valore della proprietà può essere modificato.|`false`|  
|`enumerable`|`true` o `false`. Se `enumerable` è impostato su `true`, la proprietà può essere enumerata da un'istruzione `for...in`.|`false`|  
|`configurable`|`true` o `false`. Se `configurable` è impostato su `true`, gli attributi della proprietà possono essere modificati e la proprietà può essere eliminata.|`false`|  
  
 Se il descrittore non dispone di un attributo `value`, `writable`, `get`, o `set` e il nome della proprietà specificato non esiste, viene aggiunta una proprietà di dati.  
  
 Quando l'attributo `configurable` è `false` e `writable` è `true`, gli attributi `value` e `writable` possono essere modificati.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>Proprietà dei dati aggiunte senza usare defineProperty  
 Se si aggiunge una proprietà dei dati senza usare le funzioni `Object.defineProperty`, `Object.defineProperties`, o `Object.create`, gli attributi `writable`, `enumerable`, e `configurable` sono tutti impostati su `true`. Dopo aver aggiunto la proprietà, è possibile modificarla tramite la funzione `Object.defineProperty`.  
  
 È possibile usare le modalità seguenti per aggiungere una proprietà dei dati:  
  
-   Un operatore di assegnazione (=), come in `obj.color = "white";`  
  
-   Un valore letterale di oggetto, come in `obj = { color: "white", height: 5 };`  
  
-   Una funzione di costruzione, come descritto in [Uso di costruttori per la definizione di tipi](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### <a name="accessor-properties"></a>Proprietà della funzione di accesso  
 Una *proprietà della funzione di accesso* chiama una funzione fornita dall'utente ogni volta che il valore della proprietà è impostato o recuperato. Il descrittore per una proprietà della funzione di accesso contiene un attributo `get`, un attributo `set` o entrambi.  
  
 Nella tabella seguente sono elencati gli attributi per un descrittore di proprietà della funzione di accesso.  
  
|Attributo del descrittore della funzione di accesso|Descrizione|Impostazione predefinita|  
|-----------------------------------|-----------------|-------------|  
|`get`|Una funzione che restituisce il valore della proprietà. La funzione non ha parametri.|`undefined`|  
|`set`|Una funzione che configura il valore della proprietà. Include un parametro che contiene il valore da assegnare.|`undefined`|  
|`enumerable`|`true` o `false`. Se `enumerable` è impostato su `true`, la proprietà può essere enumerata da un'istruzione `for...in`.|`false`|  
|`configurable`|`true` o `false`. Se `configurable` è impostato su `true`, gli attributi della proprietà possono essere modificati e la proprietà può essere eliminata.|`false`|  
  
 Quando una funzione di accesso `get` non è definita e viene effettuato un tentativo di accesso al valore della proprietà, viene restituito il valore `undefined`. Quando una funzione di accesso `set` non è definito e viene effettuato un tentativo di assegnare un valore alla proprietà della funzione di accesso, non accade nulla.  
  
### <a name="property-modifications"></a>Modifiche della proprietà  
 Se l'oggetto dispone già di una proprietà con il nome specificato, vengono modificati gli attributi della proprietà. Quando si modifica la proprietà, gli attributi che non sono specificati nel descrittore restano invariati.  
  
 Se l'attributo `configurable` di una proprietà esistente è `false`, la sola modifica consentita è cambiare l'attributo `writable` da `true` a `false`.  
  
 È possibile modificare una proprietà dei dati in una proprietà di accesso e viceversa. Quando si fa questo, gli attributi `configurable` e `enumerable` che non sono specificati nel descrittore sono conservati nella proprietà. Altri attributi che non sono specificati nel descrittore di vengono impostati sui valori predefiniti.  
  
 È possibile definire in modo incrementale le proprietà della funzione di accesso che possono essere configurate tramite più chiamate alla funzione `Object.defineProperty`. Per esempio, una chiamata `Object.defineProperty` può definire solo una funzione di accesso `get`. Una chiamata successiva sullo stesso nome della proprietà può definire una funzione di accesso `set`. La proprietà hanno quindi sia una funzione di accesso `get` che una funzione di accesso `set`.  
  
 Per ottenere un oggetto del descrittore che si applica a una proprietà esistente, è possibile usare la [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 È possibile usare la [Funzione Object.Seal](../../javascript/reference/object-seal-function-javascript.md) e la [Funzione Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md) per impedire la modifica degli attributi della proprietà.