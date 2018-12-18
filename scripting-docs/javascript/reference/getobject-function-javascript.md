---
title: Funzione GetObject (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getobject-function-javascript"></a>Funzione GetObject (JavaScript)
Restituisce un riferimento a un oggetto di automazione da un file.  
  
> [!NOTE]
>  Questa funzione non è supportata in Internet Explorer 9 (modalità standard) o versione successiva.  
  
## <a name="syntax"></a>Sintassi  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Parametri  
 `pathname`  
 Parametro facoltativo. Percorso completo e nome del file contenente l'oggetto da recuperare. Se `pathname` viene omesso, `class` è obbligatorio.  
  
 `class`  
 Parametro facoltativo. Classe dell'oggetto.  
  
 Il `class` argomento utilizza la sintassi `appname.objectype` e presenta le seguenti parti:  
  
 `appname`  
 Obbligatorio. Nome dell'applicazione che fornisce l'oggetto.  
  
 `objectype`  
 Obbligatorio. Tipo o classe dell'oggetto da creare.  
  
## <a name="remarks"></a>Note  
 Il `GetObject` funzione non è supportata in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o versione successiva.  
  
 Utilizzare il `GetObject` funzione per accedere a un oggetto di automazione da un file. Assegnare l'oggetto restituito da `GetObject` per la variabile oggetto. Ad esempio:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Quando viene eseguito questo codice, l'applicazione associata all'oggetto specificato `pathname` viene avviato e viene attivato l'oggetto nel file specificato. Se `pathname` è una stringa di lunghezza zero (""), `GetObject` restituisce una nuova istanza dell'oggetto del tipo specificato. Se il `pathname` viene omesso, `GetObject` restituisce un oggetto attivo del tipo specificato. Se non esiste alcun oggetto del tipo specificato, si verifica un errore.  
  
 Alcune applicazioni consentono di attivare la parte di un file. A tale scopo, aggiungere un punto esclamativo (!) alla fine del nome file e procedere con una stringa che identifica la parte del file che si desidera attivare. Per informazioni su come creare questa stringa, vedere la documentazione per l'applicazione che ha creato l'oggetto.  
  
 In un'applicazione di disegno, ad esempio, potrebbe essere più livelli per un disegno archiviato in un file. È possibile utilizzare il codice seguente per attivare un livello all'interno di un disegno denominato `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Se non si specifica la classe dell'oggetto, automazione determina quale applicazione da avviare e l'oggetto da attivare, in base al nome file che è specificato. Alcuni file, tuttavia, possono supportare più di una classe dell'oggetto. Ad esempio, un disegno potrebbe supportare tre diversi tipi di oggetti: un oggetto Application un oggetto di disegno e un oggetto barra degli strumenti, che fanno parte dello stesso file. Per specificare l'oggetto in un file a cui si desidera attivare, utilizzare l'opzione facoltativa `class` argomento. Ad esempio:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Nell'esempio precedente, `FIGMENT` è il nome di un'applicazione di disegno e `DRAWING` è uno dei tipi di oggetto supportati. Dopo un oggetto viene attivato, è possibile farvi riferimento nel codice utilizzando la variabile oggetto definita. Nell'esempio precedente, accedere alle proprietà e metodi del nuovo oggetto tramite la variabile oggetto `MyObject`. Ad esempio:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Utilizzare il `GetObject` funzione quando un'istanza dell'oggetto corrente oppure se si desidera creare l'oggetto con un file già caricato. Se è presente alcuna istanza corrente e non si desidera avviare l'oggetto con un file caricato, utilizzare il `ActiveXObject` oggetto.  
  
 Se un oggetto è stato registrato come un oggetto a istanza singola, solo un'istanza dell'oggetto viene creata, indipendentemente da come numero di volte `ActiveXObject` viene eseguita. Con un oggetto a istanza singola, `GetObject` restituisce sempre la stessa istanza quando viene chiamato con la stringa di lunghezza zero (""), sintassi e si genera un errore se il `pathname` viene omesso.  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7 e standard di Internet Explorer 8. Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)