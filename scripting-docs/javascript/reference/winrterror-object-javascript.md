---
title: Oggetto WinRTError (JavaScript) | Documenti Microsoft
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
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>Oggetto WinRTError (JavaScript)
Quando una chiamata di Windows Runtime ritorna un HRESULT che indica un errore, JavaScript lo converte in un errore speciale di Windows Runtime. È disponibile solo nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], quando Windows Runtime è disponibile, come parte dello spazio dei nomi globale di JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Note  
 Il tipo di errore di WinRTError viene usato solo per errori generati dalle API di Windows Runtime.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come viene generato e intercettato un oggetto WinRTError.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Metodi  
 L'oggetto WinRTError non ha metodi.  
  
## <a name="properties"></a>Proprietà  
 L'oggetto WinRTError ha le stesse proprietà di [oggetto Error](../../javascript/reference/error-object-javascript.md) oggetto.  
  
## <a name="requirements"></a>Requisiti  
 È supportato solo nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e non in Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)