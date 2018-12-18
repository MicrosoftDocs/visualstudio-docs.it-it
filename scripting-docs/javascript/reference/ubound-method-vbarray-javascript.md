---
title: Metodo UBound (VBArray) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ubound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ubound method
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfb87cf3fd552c329635a3ca3e974c84a1324bfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ubound-method-vbarray-javascript"></a>Metodo ubound (VBArray) (JavaScript)
Restituisce il valore di indice più elevato usato nella dimensione specificata dell'oggetto VBArray.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
safeArray.ubound(dimension)   
```  
  
## <a name="parameters"></a>Parametri  
 *safeArray*  
 Obbligatorio. Un oggetto VBArray.  
  
 `dimension`  
 Facoltativo. La dimensione dell'oggetto VBArray per il quale si desidera recuperare l'indice più elevato. Se omesso, `ubound` si comporta come se venisse passato il valore 1.  
  
## <a name="remarks"></a>Note  
 Se l'oggetto VBArray è vuoto, il metodo `ubound` restituisce non definito. Se `dim` è maggiore del numero di dimensioni dell'oggetto VBArray o è negativo, il metodo genera un errore del tipo "Indice non incluso nell'intervallo".  
  
## <a name="example"></a>Esempio  
 L'esempio seguente si compone di tre parti: La prima parte è il codice VBScript per creare una matrice protetta di Visual Basic. La seconda parte è il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che determina il numero di dimensioni della matrice protetta e il limite superiore di ogni dimensione. Entrambe queste parti vanno inserite le \<HEAD > della sezione di una pagina HTML. La terza parte è il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice che va inserito nella \<corpo > per eseguire le altre due parti.  
  
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
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
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
 [Metodo LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Metodo toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)