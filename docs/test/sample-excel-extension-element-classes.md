---
title: 'Estensione Excel di esempio: classi Element'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a254f85a27c650bf8d8b64d2460ebad88e3befc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-element-classes"></a>Estensione Excel di esempio: classi Element
L'estensione usa classi derivate da <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> e rappresenta i controlli foglio di lavoro e cella in [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 L'elemento di base per questa estensione è `ExcelElement`. La classe `ExcelWorksheetElement` e la classe `ExcelCellElement` ereditano da tale elemento.

## <a name="element-and-elementinformation-classes"></a>Classi Element ed ElementInformation
 `Element` è la classe di base per tutti gli elementi dell'interfaccia utente per l'estensione Excel ed eredita dalla classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>. `ElementInformation` è la classe di base per le classi di informazioni dell'elemento nell'esempio e non contiene membri.

#### <a name="simple-properties-and-methods"></a>Proprietà e metodi semplici
 Questi membri restituiscono valori semplici, ad esempio il valore della proprietà `Name` o il valore della proprietà `ClassName`, e il codice è chiaro e semplice da leggere. Alcuni valori vengono restituiti tramite la classe `Utility`, illustrata più avanti. Altri restituiscono `null` perché non sono pertinenti in questa estensione di esempio. Due membri sono particolarmente interessanti: la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> e il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.

#### <a name="queryid-property"></a>Proprietà QueryId
 Questa proprietà restituisce una condizione costituita da coppie nome-valore di proprietà, che identificano in modo univoco il controllo durante la riproduzione. Per ogni classe del controllo derivata, lo sviluppatore deve eseguire l'override di questa proprietà per restituire un oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> che il framework può usare per trovare il controllo nell'interfaccia utente.

#### <a name="cacheproperties-method"></a>Metodo CacheProperties
 Questo metodo viene chiamato dal framework di test durante il processo di registrazione per comunicare all'elemento di salvare uno snapshot di proprietà importanti. In questo modo, le proprietà sono disponibili anche quando l'effettivo controllo dell'interfaccia utente non è più sullo schermo.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>Classi WorksheetElement e WorksheetInformation
 La classe `WorksheetElement` rappresenta un foglio di lavoro di Excel nel framework di test ed eredita dalla classe di base `Element`. Tre proprietà vengono sottoposte a override per fornire informazioni specifiche sull'oggetto foglio di lavoro di Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.

 A questa classe viene applicato anche l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> per renderla visibile a COM.

 La classe `WorksheetInformation` rappresenta le informazioni su un foglio di lavoro di Excel. Dispone di un solo membro, la proprietà `SheetName`, che è sufficiente per questo esempio.

## <a name="cellelement-and-cellinformation-classes"></a>Classi CellElement e CellInformation
 La classe `CellElement` rappresenta una cella di Excel ed eredita dalla classe di base `Element`. L'unico membro sottoposto a override è la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, che restituisce un oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> che usa le proprietà `RowIndex` e `ColumnIndex` per identificare la cella.

## <a name="utilities-and-excelutilities-classes"></a>Classi Utilities ed ExcelUtilities
 La classe interna `ExcelUtilities` fornisce alcuni valori costanti, ad esempio il nome della tecnologia, e un metodo che determina se l'handle di finestra fornito rappresenta un foglio di lavoro di Excel.

 La classe `Utilities` dispone di metodi helper che restituiscono un'ampia varietà di informazioni sull'interfaccia utente. Alcuni metodi usano chiamate dirette a DLL di sistema esterne, ad esempio **USER32.DLL** e **OLEACC.DLL**, per ottenere gli handle di finestra dall'interfaccia utente **.**

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
