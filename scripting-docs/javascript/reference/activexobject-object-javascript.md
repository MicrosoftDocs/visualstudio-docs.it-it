---
title: Oggetto ActiveXObject (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ActiveXObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ActiveXObject object
- Automation objects, ActiveXObject objects
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bb743aeab563f7d7711e4caa9a0fcf0b45ff58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="activexobject-object-javascript"></a>Oggetto ActiveXObject (JavaScript)
Abilita e restituisce un riferimento a un oggetto di automazione.  
  
 Questo oggetto viene utilizzato per istanziare gli oggetti di automazione e non dispone di membri.  
  
> [!WARNING]
>  Questo oggetto è un'estensione Microsoft ed è supportato in Internet Explorer, non solo nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## <a name="parameters"></a>Parametri  
 `newObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `ActiveXObject` è assegnato.  
  
 `servername`  
 Obbligatorio. Nome dell'applicazione che fornisce l'oggetto.  
  
 `typename`  
 Obbligatorio. Tipo o classe dell'oggetto da creare.  
  
 `location`  
 Parametro facoltativo. Nome del server di rete in cui verrà creato l'oggetto.  
  
## <a name="remarks"></a>Note  
 I server di automazione forniscono almeno un tipo di oggetto. Un programma di elaborazione di testi, ad esempio, può fornire un oggetto applicazione, un oggetto documento e un oggetto barra degli strumenti.  
  
 È possibile identificare i valori `servername.typename` su un computer host nella chiave del Registro di sistema `HKEY_CLASSES_ROOT`. Di seguito sono riportati alcuni esempi di valori disponibili a seconda dei programmi installati:  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Gli oggetti ActiveX possono presentare problemi di sicurezza. Per utilizzare `ActiveXObject`, potrebbe essere necessario modificare le impostazioni di sicurezza in Internet Explorer per l'area di sicurezza rilevante. Ad esempio, per l'area Intranet locale, generalmente è necessario modificare un'impostazione personalizzata su "Inizializza ed esegui script controlli ActiveX non contrassegnati come sicuri per lo script".  
  
 Per identificare i membri di un oggetto di automazione che è possibile utilizzare nel codice, è necessario utilizzare un Visualizzatore oggetti COM, ad esempio il [Visualizzatore oggetti OLE/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), se la documentazione di riferimento non è disponibile per l'oggetto di automazione.  
  
 Per creare un oggetto di automazione, assegnare il nuovo oggetto `ActiveXObject` a una variabile oggetto:  
  
```JavaScript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Questo codice avvia l'applicazione creando l'oggetto (in questo caso, un foglio di lavoro di Microsoft Excel). Una volta che l'oggetto è stato creato, è possibile fare riferimento a quest'ultimo nel codice utilizzando la variabile oggetto definita. Nell'esempio di codice seguente è possibile accedere alle proprietà e ai metodi del nuovo oggetto tramite la variabile oggetto `ExcelSheet` e tramite gli altri oggetti Excel, tra cui l'oggetto Application e la raccolta ActiveSheet.Cells.  
  
```JavaScript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9, standard di Internet Explorer 10, standard di Internet Explorer 11. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  La creazione di `ActiveXObject` su un server remoto non è supportata nella [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o nelle versioni successive.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione GetObject](../../javascript/reference/getobject-function-javascript.md)   
 [Autenticazione univoco tramite app di esempio Magic HTML5/WCF](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)