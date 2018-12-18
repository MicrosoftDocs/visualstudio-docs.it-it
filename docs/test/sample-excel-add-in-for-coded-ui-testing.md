---
title: Componente aggiuntivo di Excel di esempio per i test codificati dell'interfaccia utente | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: aee4f7bcf827fc7d42b9c885d78b83df1ea54fd3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Componente aggiuntivo di Excel di esempio per i test codificati dell'interfaccia utente
Questo componente aggiuntivo di esempio per [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] è specificamente progettato per supportare i test codificati dell'interfaccia utente dei fogli di lavoro di Excel registrati ed eseguiti in Visual Studio Enterprise. Per creare il componente aggiuntivo, si usa Visual Studio Tools per Office.

 Per altre informazioni su come creare un componente aggiuntivo di Excel, vedere [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) o cercare "componente aggiuntivo Excel" in MSDN.

 Anche se il componente aggiuntivo per Excel non è l'argomento principale di questi documenti sull'estensione dei test codificati dell'interfaccia utente per Excel, alcuni commenti possono essere utili.

 Parti importanti di questo componente aggiuntivo:

-   Classe `ThisAddIn`: gestisce il canale Servizi remoti .NET tra `ExcelUICommunicator` e l'[estensione di esempio per i test codificati dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md).

-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`: certificato di sicurezza per il test del componente aggiuntivo.

-   Classe `ExcelUICommunicator`: questa classe implementa l'interfaccia `IExcelUICommunication`.

## <a name="thisaddin-class"></a>Classe ThisAddIn
 La maggior parte degli elementi di questa classe viene effettivamente generata da Visual Studio Tools per Office nel file `ThisAddIn.Designer.cs` quando si crea il progetto Componente aggiuntivo di Excel.

 I membri che è necessario implementare sono i gestori eventi: `ThisAddIn_Startup()` e `ThisAddIn_Shutdown()`, il cui scopo è inizializzare o chiudere il canale Servizi remoti .NET usato da `ExcelUICommunicator`.

## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx
 Questo file contiene un certificato di sicurezza temporaneo che viene generato da Visual Studio Tools per Office e concede all'assembly del componente aggiuntivo l'autorizzazione per operare nel processo di Excel per il test del componente aggiuntivo e dell'estensione. È consigliabile eliminare questo certificato e crearne uno nuovo nella scheda **Firma** della finestra **Proprietà** del progetto. In alternativa, associare il proprio certificato di test.

## <a name="exceluicommunicator-class"></a>Classe ExcelUICommunicator
 Questa classe implementa l'interfaccia `IExcelUITestCommunication` e ottiene dal modello a oggetti di Excel le informazioni dell'interfaccia utente richieste. Per altre informazioni, vedere [Interfaccia Excel Communicator di esempio](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Vedere anche

- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)
- [Sviluppo di Office e SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
