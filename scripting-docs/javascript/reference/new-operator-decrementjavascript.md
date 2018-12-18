---
title: Operatore new (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>Operatore new (JavaScript)
Crea un nuovo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Parametri  
 `constructor`  
 Obbligatorio. Il costruttore dell'oggetto. Le parentesi che possono essere omesso se il costruttore non accetta argomenti.  
  
 `arguments`  
 Parametro facoltativo. Eventuali argomenti da passare al costruttore del nuovo oggetto.  
  
## <a name="remarks"></a>Note  
 Il `new` operatore esegue le attività seguenti:  
  
-   Crea un oggetto senza membri.  
  
-   Chiama il costruttore dell'oggetto, passando un puntatore all'oggetto appena creato come il `this` puntatore.  
  
-   Quindi, il costruttore inizializza l'oggetto in base agli argomenti passati al costruttore.  
  
 Questi sono esempi di utilizzi validi del **nuova** operatore.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)