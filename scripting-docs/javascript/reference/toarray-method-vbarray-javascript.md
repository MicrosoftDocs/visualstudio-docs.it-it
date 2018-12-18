---
title: Metodo toArray (VBArray) (JavaScript) | Documenti Microsoft
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
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>Metodo toArray (VBArray) (JavaScript)
Restituisce una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] standard convertita da un oggetto VBArray.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Note  
 Il riferimento *safeArray* richiesto è un oggetto VBArray.  
  
 La conversione trasforma l'oggetto VBArray multidimensionale in una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] unidimensionale. Ogni successiva dimensione viene aggiunta alla fine di quella precedente. Ad esempio, un oggetto VBArray a tre dimensioni e tre elementi in ogni dimensione viene convertito in una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] come indicato di seguito:  
  
 Si supponga che contiene l'oggetto VBArray contiene: (1, 2, 3), (4, 5, 6), (7, 8, 9). Dopo la conversione, la matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contiene: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Attualmente non è possibile convertire una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in un oggetto VBArray.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente si compone di tre parti: La prima parte è il codice VBScript per creare una matrice protetta di Visual Basic. La seconda parte è il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che converte la matrice protetta di Visual Basic in una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Entrambe queste parti vanno inserite le \<HEAD > della sezione di una pagina HTML. La terza parte è il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice che va inserito nella \<corpo > per eseguire le altre due parti.  
  
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
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
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
 [Metodo ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)