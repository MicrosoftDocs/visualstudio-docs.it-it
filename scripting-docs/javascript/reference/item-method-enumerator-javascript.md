---
title: Metodo Item (Enumerator) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: item
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Item method
ms.assetid: a88e93f2-42df-4578-a4f9-0760bd074185
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94275b2c82f199c96ef2d6c7d667fd27fba2702d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="item-method-enumerator-javascript"></a>Metodo item (Enumerator) (JavaScript)
Restituisce l'elemento corrente nella raccolta.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
enumObj.item()   
```  
  
## <a name="remarks"></a>Note  
 Il riferimento *enumObj* obbligatorio è qualsiasi oggetto `Enumerator` .  
  
 Il metodo **item** restituisce l'elemento corrente. Se la raccolta è vuota o l'elemento corrente è non definito, il metodo restituisce **undefined**.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente il metodo **item** viene usato per restituire un membro della raccolta `Drives` .  
  
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
 [Metodo moveFirst (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [Metodo moveNext (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)