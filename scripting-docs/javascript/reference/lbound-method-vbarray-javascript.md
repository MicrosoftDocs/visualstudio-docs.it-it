---
title: Metodo LBound (VBArray) (JavaScript) | Documenti Microsoft
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
- lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="lbound-method-vbarray-javascript"></a>Metodo lbound (VBArray) (JavaScript)
Restituisce il valore di indice più basso utilizzato nella dimensione specificata di un oggetto VBArray.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>Parametri  
 *safeArray*  
 Obbligatorio. Un oggetto VBArray.  
  
 `dimension`  
 Parametro facoltativo. La dimensione dell'oggetto VBArray per cui si desidera recuperare l'indice del limite inferiore. Se omesso, `lbound` si comporta come se venisse passato il valore 1.  
  
## <a name="remarks"></a>Note  
 Se l'oggetto VBArray è vuoto, il metodo `lbound` restituisce non definito. Se `dimension` è maggiore del numero di dimensioni dell'oggetto VBArray o è negativo, il metodo genera un errore del tipo "Indice non incluso nell'intervallo".  
  
## <a name="example"></a>Esempio  
 L'esempio seguente si compone di tre parti: La prima parte è il codice VBScript per creare una matrice protetta di Visual Basic. La seconda parte è [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] il codice che determina il numero di dimensioni della matrice protetta e il limite inferiore di ogni dimensione. Poiché la matrice sicura viene creata in VBScript anziché in Visual Basic, è possibile che il limite inferiore sarà sempre zero. Entrambe queste parti vanno inserite le \<HEAD > della sezione di una pagina HTML. La terza parte è il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice che va inserito nella \<corpo > per eseguire le altre due parti.  
  
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
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Metodo getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Metodo toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Metodo ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)