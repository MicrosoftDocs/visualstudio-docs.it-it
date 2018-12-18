---
title: Metodo moveNext (Enumerator) (JavaScript) | Documenti Microsoft
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
- moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="movenext-method-enumerator-javascript"></a>Metodo moveNext (Enumerator) (JavaScript)
Sposta l'elemento corrente sull'elemento successivo nella raccolta.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>Note  
 Il riferimento *enumObj* obbligatorio è qualsiasi oggetto `Enumerator` .  
  
 Se l'enumeratore si trova alla fine della raccolta o la raccolta è vuota, l'elemento corrente viene impostato su non definito.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il metodo **moveNext** metodo viene usato per passare all'elemento successivo nella raccolta `Drives` :  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo atEnd (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Metodo Item (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Metodo moveFirst (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)