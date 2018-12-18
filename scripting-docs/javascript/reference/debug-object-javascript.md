---
title: Oggetto debug (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Oggetto Debug (JavaScript)
Oggetto globale intrinseco che invia l'output a un debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Note  
 Non creare l'istanza l'oggetto Debug. È possibile accedere a tutte le proprietà e metodi chiamando `function`.  
  
 Esistono diversi modi per eseguire il debug di Internet Explorer e delle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] le funzioni `write` e `writeln` dell'oggetto `Debug` visualizzano le stringhe nella finestra di dialogo **Output** di Visual Studio in fase di esecuzione. Per ulteriori informazioni sul debug [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] App, vedere [il Debug di App universali di Windows in Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Per eseguire il debug degli script di Internet Explorer, è necessario che sia installato un debugger di script e che lo script sia eseguito in modalità debug. Internet Explorer 8 e le versioni successive includono il debugger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Se si usa una versione precedente di Internet Explorer, vedere [Procedura: Attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Se non viene eseguito il debug dello script, le funzioni non hanno alcun effetto.  
  
## <a name="example"></a>Esempio  
 Questo esempio usa la funzione `write` per visualizzare il valore della variabile.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Costanti  
 [Costanti Debug](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Proprietà  
 [Proprietà di debug. debuggerenabled](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Proprietà Debug. setnonusercodeexceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Funzioni  
 [Funzione debug. mstraceasynccallbackstarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Funzione debug. mstraceasynccallbackcompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Funzione debug. mstraceasyncoperationcompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Funzione debug. mstraceasyncoperationstarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Funzione debug. msupdateasynccallbackrelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Funzione debug. Write](../../javascript/reference/debug-write-function-javascript.md) &#124; [Funzione debug. writeln](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione debugger](../../javascript/reference/debugger-statement-javascript.md)