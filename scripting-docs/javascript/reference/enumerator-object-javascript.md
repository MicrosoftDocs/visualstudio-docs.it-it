---
title: Oggetto Enumerator (JavaScript) | Documenti Microsoft
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
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Oggetto Enumerator (JavaScript)
Abilita l'enumerazione di elementi di una raccolta.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer e non nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Parametri  
 `enumObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Enumerator` è assegnato.  
  
 `collection`  
 Facoltativo. Qualsiasi oggetto Collection.  
  
## <a name="remarks"></a>Note  
 Le raccolte differiscono dalle matrici in quanto i membri di una raccolta non sono direttamente accessibili. Invece di usare indici, come si farebbe con le matrici, è possibile spostare il puntatore dell'elemento corrente solo sul primo elemento o sull'elemento successivo all'interno della raccolta.  
  
 L'oggetto `Enumerator` fornisce un modo per accedere a qualsiasi membro di una raccolta e si comporta in modo analogo all'istruzione `For...Each` in VBScript.  
  
## <a name="example"></a>Esempio  
 Il codice seguente mostra l'uso dell'oggetto `Enumerator` :  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Proprietà  
 L'oggetto `Enumerator` non ha alcuna proprietà.  
  
## <a name="methods"></a>Metodi  
 [Metodo atEnd](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [metodo item](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [metodo moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext (metodo)](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)