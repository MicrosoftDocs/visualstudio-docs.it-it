---
title: Oggetto Math (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="math-object-javascript"></a>Oggetto Math (JavaScript)
Oggetto intrinseco che fornisce funzioni e costanti matematiche di base.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>Parametri  
 *proprietà*  
 Obbligatorio. Nome di una delle proprietà del **matematiche**. .  
  
 *metodo*  
 Obbligatorio. Nome di uno dei metodi del **matematiche**. .  
  
## <a name="remarks"></a>Note  
 Il **matematiche** oggetto non può essere creato utilizzando il **nuova** (operatore) e restituisce un errore se si tenta di eseguire questa operazione. Il motore di script crea questo oggetto durante il caricamento. Tutti i metodi e le proprietà dell'oggetto sono disponibili per lo script in qualsiasi momento.  
  
## <a name="requirements"></a>Requisiti  
 L'oggetto `Math` è stato introdotto in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Math`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante Math. e](../../javascript/reference/math-constants-javascript.md)|Costante matematica e. Si tratta del numero di Eulero, la base dei logaritmi naturali.|  
|[Math.LN2 (costante)](../../javascript/reference/math-constants-javascript.md)|Logaritmo naturale di 2.|  
|[Costante Math. LN10](../../javascript/reference/math-constants-javascript.md)|Logaritmo naturale di 10.|  
|[Costante Math. LOG2E](../../javascript/reference/math-constants-javascript.md)|Logaritmo in base 2 di e.|  
|[Costante Math. LOG10E](../../javascript/reference/math-constants-javascript.md)|Logaritmo in base 10 di e.|  
|[Costante Math. PI](../../javascript/reference/math-constants-javascript.md)|Pi greco. Rapporto tra la circonferenza del cerchio e il suo diametro.|  
|[Costante Math. SQRT1_2](../../javascript/reference/math-constants-javascript.md)|Radice quadrata di 0,5 oppure uno diviso per la radice quadrata di 2.|  
|[Costante Math. SQRT2](../../javascript/reference/math-constants-javascript.md)|Radice quadrata di 2.|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>Funzioni  
 Nella tabella seguente sono elencate le funzioni dell'oggetto `Math`.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione Math.abs](../../javascript/reference/math-abs-function-javascript.md)|Restituisce il valore assoluto di un numero.|  
|[Funzione Math.acos](../../javascript/reference/math-acos-function-javascript.md)|Restituisce l'arcocoseno di un numero.|  
|[Funzione Math.acosh](../../javascript/reference/math-acosh-function-javascript.md)|Restituisce l'arcocoseno iperbolico (o coseno iperbolico inverso) di un numero.|  
|[Funzione Math.asin](../../javascript/reference/math-asin-function-javascript.md)|Restituisce l'arcoseno di un numero.|  
|[Funzione Math.asinh](../../javascript/reference/math-asinh-function-javascript.md)|Restituisce il seno iperbolico inverso di un numero.|  
|[Funzione Math.atan](../../javascript/reference/math-atan-function-javascript.md)|Restituisce l'arcotangente di un numero.|  
|[Funzione Math.atan2](../../javascript/reference/math-atan2-function-javascript.md)|Restituisce l'angolo (in radianti) dall'asse X a un punto rappresentato dalle coordinate y e x specificate.|  
|[Funzione Math.atanh](../../javascript/reference/math-atanh-function-javascript.md)|Restituisce la tangente iperbolica inversa di un numero.|  
|[Funzione Math.ceil](../../javascript/reference/math-ceil-function-javascript.md)|Restituisce il valore Integer più piccolo che è maggiore o uguale all'espressione numerica specificata.|  
|[Funzione Math.cos](../../javascript/reference/math-cos-function-javascript.md)|Restituisce il coseno di un numero.|  
|[Funzione Math.cosh](../../javascript/reference/math-cosh-function-javascript.md)|Restituisce il coseno iperbolico di un numero.|  
|[Funzione Math.exp](../../javascript/reference/math-exp-function-javascript.md)|Restituisce *e* (base dei logaritmi naturali) elevato a potenza.|  
|[Funzione Math.expm1](../../javascript/reference/math-expm1-function-javascript.md)|Restituisce il risultato della sottrazione di 1 da e (base dei logaritmi naturali) elevata a una potenza.|  
|[Funzione Math.floor](../../javascript/reference/math-floor-function-javascript.md)|Restituisce il valore Integer più grande che è minore o uguale all'espressione numerica fornita.|  
|[Funzione Math.hypot](../../javascript/reference/math-hypot-function-javascript.md)|Restituisce la radice quadrata della somma dei quadrati degli argomenti.|  
|[Funzione Math.imul](../../javascript/reference/math-imul-function-javascript.md)|Restituisce il prodotto di due numeri che vengono considerati come valori integer firmati a 32 bit.|  
|[Funzione Math.log](../../javascript/reference/math-log-function-javascript.md)|Restituisce il logaritmo naturale di un numero.|  
|[Funzione Math.log1p](../../javascript/reference/math-log1p-function-javascript.md)|Restituisce il logaritmo naturale di 1 + un numero.|  
|[Funzione Math.log10](../../javascript/reference/math-log10-function-javascript.md)|Restituisce il logaritmo in base 10 di un numero.|  
|[Funzione Math.log2](../../javascript/reference/math-log2-function-javascript.md)|Restituisce il logaritmo in base 2 di un numero.|  
|[Funzione Math.max](../../javascript/reference/math-max-function-javascript.md)|Restituisce la maggiore di due espressioni numeriche specificate.|  
|[Funzione Math.min](../../javascript/reference/math-min-function-javascript.md)|Restituisce il minore di due numeri specificati.|  
|[Funzione Math.pow](../../javascript/reference/math-pow-function-javascript.md)|Restituisce il valore di un'espressione di base elevata a una potenza specificata.|  
|[Funzione Math.random](../../javascript/reference/math-random-function-javascript.md)|Restituisce un numero pseudocasuale compreso tra 0 e 1.|  
|[Funzione Math.round](../../javascript/reference/math-round-function-javascript.md)|Restituisce un'espressione numerica specificata arrotondata al numero intero più vicino.|  
|[Funzione Math.sign](../../javascript/reference/math-sign-function-javascript.md)|Restituisce il segno di un numero, indicante se il numero è positivo, negativo o 0.|  
|[Funzione Math.sin](../../javascript/reference/math-sin-function-javascript.md)|Restituisce il seno di un numero.|  
|[Funzione Math.sinh](../../javascript/reference/math-sinh-function-javascript.md)|Restituisce il seno iperbolico inverso di un numero.|  
|[Funzione Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Restituisce la radice quadrata di un numero.|  
|[Funzione Math.tan](../../javascript/reference/math-tan-function-javascript.md)|Restituisce la tangente di un numero.|  
|[Funzione Math.tanh](../../javascript/reference/math-tanh-function-javascript.md)|Restituisce la tangente iperbolica inversa di un numero.|  
|[Funzione Math.trunc](../../javascript/reference/math-trunc-function-javascript.md)|Restituisce la parte intera di un numero, rimuovendo eventuali cifre frazionarie.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti JavaScript](../../javascript/reference/javascript-objects.md)   
 [Oggetto Number](../../javascript/reference/number-object-javascript.md)