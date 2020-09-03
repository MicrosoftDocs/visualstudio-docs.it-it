---
title: Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4cac9981a582d5ba9527e0f8dc47d14b6fba18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851759"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il framework di test per i test codificati dell'interfaccia utente e le registrazioni delle azioni non supportano tutte le interfacce utente disponibili, e quindi potrebbero non supportare l'interfaccia utente specifica di cui eseguire il test. Ad esempio, non si può creare immediatamente un test codificato dell'interfaccia utente o una registrazione delle azioni per un foglio di calcolo di [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Si può però creare un'estensione personalizzata del framework dei test codificati dell'interfaccia utente che supporterà l'interfaccia utente specifica sfruttando l'estendibilità del framework stesso. L'argomento seguente viene fornito un esempio che illustra come estendere il framework per supportare la creazione di test e le registrazioni delle azioni per [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Per altre informazioni sulle piattaforme supportate, vedere [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

 **Requisiti**

- Visual Studio Enterprise

  In questa sezione viene presentata un'estensione del test codificato dell'interfaccia utente in grado di registrare e riprodurre test di Fogli di lavoro di Excel. Ogni parte dell'estensione viene spiegata sia in questa sezione che nei commenti del codice, a beneficio degli sviluppatori che vogliono creare una tale estensione.

  ![Architettura di test dell'interfaccia utente](../test/media/ui-testarch.png "UI_TestArch") Panoramica dell'architettura

## <a name="download-the-sample"></a>Scaricare l'esempio
 L'esempio è costituito da quattro progetti nella soluzione `CodedUIExtensibilitySample.sln`:

- CodedUIextensibilitySample

- ExcelCodedUIAddInHelper

- ExcelUICommunicationHelper

- SampleTestProject

  È possibile scaricare l'esempio da questo [post di blog](https://blogs.msdn.com/b/gautamg/archive/2010/01/05/3-introducing-sample-excel-extension.aspx).

> [!NOTE]
> L'esempio è concepito per Microsoft Excel 2010. Potrebbe funzionare con altre versioni di Microsoft Excel, ma non è attualmente supportato.

## <a name="details-about-the-sample"></a>Dettagli sull'esempio
 Nelle sezioni seguenti vengono fornite informazioni sull'esempio e sulla relativa struttura.

### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Componente aggiuntivo di Microsoft Excel: ExcelCodedUIAddinHelper
 Questo progetto include un componente aggiuntivo che viene eseguito nel processo di Excel. Per una breve panoramica del progetto del componente aggiuntivo, vedere [Componente aggiuntivo di Excel di esempio per i test codificati dell'interfaccia utente](../test/sample-excel-add-in-for-coded-ui-testing.md).

 Per altre informazioni, vedere [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).

### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Comunicazione con l'interfaccia utente di Excel: ExcelUIcommunicationHelper
 Questo progetto include l'interfaccia `IExcelUICommunication` e le classi di informazioni che vengono usate per lo scambio dei dati tra il framework dei test codificati dell'interfaccia utente ed Excel. Per altre informazioni, vedere [Interfaccia Excel Communicator di esempio](../test/sample-excel-communicator-interface.md).

### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Estensione del test codificato dell'interfaccia utente: CodedUIExentsibilitySample
 Questo progetto include le classi personalizzate usate nei test di un foglio di lavoro di Excel. Il codice per ognuna di queste classi è facilmente comprensibile. Viene comunque fornita una breve descrizione di ogni classe personalizzata. Per altre informazioni, vedere [Estensione di esempio per i test codificati dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md).

### <a name="deploying-your-add-in-and-extension"></a>Distribuzione del componente aggiuntivo e dell'estensione
 Dopo avere creato tutti i progetti e tutti gli oggetti, eseguire il file `CopyDrop.bat` fornito come amministratore. Questo file copia i file DLL e PDB di `ExcelCodedUIAddinHelper` in:

 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", dove il numero di versione potrebbe essere 11.0, 12.0 e così via a seconda della versione di Visual Studio.

 I file DLL e PDB di `ExcelUICommunicationHelper` vengono copiati in `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.

 Potrebbe essere necessario modificare i percorsi esatti per la copia, ma non è richiesta alcuna installazione aggiuntiva. In un computer a 64 bit usare il prompt dei comandi a 32 bit di Visual Studio Enterprise per eseguire il file `CopyDrop.bat`.

### <a name="testing-excel-with-the-sampletestproject"></a>Test di Excel con SampleTestProject
 È possibile eseguire il test nel progetto di test fornito che usa una versione specifica di Excel che potrebbe non essere disponibile oppure creare un progetto di test e registrare un test personalizzato. Per altre informazioni, vedere [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Procedure consigliate per i test codificati dell'interfaccia utente](../test/best-practices-for-coded-ui-tests.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
