---
title: Oggetto WeakSet (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="weakset-object-javascript"></a>Oggetto WeakSet (JavaScript)
Raccolta di oggetti univoci che possono essere di qualsiasi tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Note  
 Se si tenta di aggiungere un elemento non univoco a un oggetto `WeakSet`, il nuovo oggetto non verrà aggiunto alla raccolta.  
  
 Diversamente da `Set`, è possibile aggiungere solo oggetti alla raccolta. Non è possibile aggiungere valori arbitrari alla raccolta.  
  
 In un `WeakSet` dell'oggetto, i riferimenti agli oggetti nel set di contenuti 'debole'. Questo significa che `WeakSet` non impedirà il verificarsi di un'operazione di Garbage Collection sugli oggetti. Quando non sono presenti riferimenti (diversi da `WeakSet`) agli oggetti, Garbage Collector potrebbe raccogliere gli oggetti.  
  
 `WeakSet` (o `WeakMap`) può essere utile in alcuni scenari che comportano la memorizzazione nella cache di oggetti o metadati di oggetti. Ad esempio, i metadati per oggetti non estendibili possono essere archiviati in un oggetto `WeakSet` oppure è possibile creare una cache di immagini utente usando `WeakSet`.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `WeakSet`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|costruttore|Specifica la funzione che crea un set.|  
|prototipo|Restituisce un riferimento al prototipo per un set.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `WeakSet`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|aggiunta|Aggiunge un elemento a un set.|  
|elimina|Rimuove un elemento specificato da un set.|  
|has|Restituisce `true` se il set contiene un elemento specificato.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come aggiungere membri a un set e quindi verificare che siano stati aggiunti.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]