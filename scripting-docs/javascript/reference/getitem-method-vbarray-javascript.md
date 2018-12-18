---
title: Metodo getItem (VBArray) (JavaScript) | Documenti Microsoft
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
- getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>Metodo getItem (VBArray) (JavaScript)
Restituisce l'elemento nella posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Parametri  
 *safeArray*  
 Obbligatorio. Un oggetto VBArray.  
  
 *dimensione1,..., dimensioneN*  
 Specifica la posizione esatta dell'elemento desiderato dell'oggetto VBArray. *n* è uguale al numero di dimensioni dell'oggetto VBArray.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente si compone di tre parti: La prima parte è il codice VBScript per creare una matrice protetta di Visual Basic. La seconda parte è il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che esegue un'iterazione sulla matrice protetta di Visual Basic e stampa il contenuto di ciascun elemento. Entrambe queste parti vanno inserite le \<HEAD > della sezione di una pagina HTML. La terza parte è il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice che va inserito nella \<corpo > per eseguire le altre due parti.  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Metodo LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Metodo toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Metodo ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)