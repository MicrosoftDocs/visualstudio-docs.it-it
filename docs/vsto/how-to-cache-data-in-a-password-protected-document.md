---
title: 'Procedura: memorizzare nella Cache i dati in un documento protetto da Password | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71ce65cd253ea6473a07a98542449a1e47ae9d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procedura: memorizzare dati nella cache di un documento protetto da password
  Se si aggiungono dati alla cache di dati in un documento o una cartella di lavoro è protetta con una password, è possibile che le modifiche ai dati memorizzati nella cache non vengono salvate automaticamente. È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>La memorizzazione nella cache nei documenti di Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Per memorizzare i dati in un documento di Word protetto da password  
  
1.  Nel `ThisDocument` classe, contrassegnare un campo pubblico o una proprietà da memorizzare nella cache. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  
  
2.  Eseguire l'override di <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo la `ThisDocument` classe e rimuovere la protezione dal documento.  
  
     Quando il documento viene salvato, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per fornire all'utente la possibilità di rimuovere la protezione del documento. In questo modo le modifiche ai dati memorizzati nella cache da salvare.  
  
3.  Eseguire l'override di <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo la `ThisDocument` classe e riapplicare la protezione del documento.  
  
     Dopo che il documento viene salvato, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per fornire all'utente la possibilità di riapplicare la protezione del documento.  
  
### <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come memorizzare nella cache i dati in un documento di Word protetto da password. Prima che il codice consente di rimuovere la protezione nel <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo salva corrente <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valore, in modo che sia possibile riapplicare lo stesso tipo di protezione nel <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Compilazione del codice  
 Aggiungere questo codice per la `ThisDocument` classe nel progetto. Questo codice presuppone che la password viene archiviata in un campo denominato `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>La memorizzazione nella cache nelle cartelle di lavoro di Excel  
 Nei progetti di Excel, questa procedura è necessaria solo quando si protegge l'intera cartella di lavoro con una password utilizzando il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodo. Questa procedura non è necessaria se si protegge solo un foglio di lavoro specifico con una password utilizzando il <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodo.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Per memorizzare i dati in una cartella di lavoro di Excel che è protetta con una password  
  
1.  Nel `ThisWorkbook` classe o una del `Sheet` *n* classi, contrassegnare un campo pubblico o una proprietà da memorizzare nella cache. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  
  
2.  Eseguire l'override di <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo la `ThisWorkbook` classe e rimuovere la protezione dalla cartella di lavoro.  
  
     Quando la cartella di lavoro viene salvato, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per fornire all'utente la possibilità di rimuovere la protezione della cartella di lavoro. In questo modo le modifiche ai dati memorizzati nella cache da salvare.  
  
3.  Eseguire l'override di <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo la `ThisWorkbook` classe e riapplicare la protezione del documento.  
  
     Dopo aver salvato la cartella di lavoro, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per fornire all'utente la possibilità di riapplicare la protezione per la cartella di lavoro.  
  
### <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come memorizzare nella cache i dati in una cartella di lavoro di Excel che è protetta con una password. Prima che il codice consente di rimuovere la protezione nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo salva corrente <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> e <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> valori, in modo che sia possibile riapplicare lo stesso tipo di protezione nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Compilazione del codice  
 Aggiungere questo codice per la `ThisWorkbook` classe nel progetto. Questo codice presuppone che la password viene archiviata in un campo denominato `securelyStoredPassword`.  
  
## <a name="see-also"></a>Vedere anche  
 [La memorizzazione nella cache di dati](../vsto/caching-data.md)   
 [Procedura: memorizzare nella Cache di dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: Memorizzare nella cache a livello di codice un'origine dati di un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  