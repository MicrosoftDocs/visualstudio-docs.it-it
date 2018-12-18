---
title: "Procedura: memorizzare nella Cache a livello di codice di un'origine dati in un documento di Office | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29451bab5caeeaf3f9de0b9344ae52430ec045a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Procedura: memorizzare nella cache a livello di codice un'origine dati di un documento di Office
  È possibile aggiungere un oggetto dati a livello di codice per la cache dei dati in un documento mediante una chiamata di `StartCaching` elemento metodo di un host, ad esempio un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, o <xref:Microsoft.Office.Tools.Excel.Worksheet>. Per rimuovere un oggetto dati dalla cache dei dati, chiamare il `StopCaching` metodo di un elemento host.  
  
 Il `StartCaching` (metodo) e `StopCaching` metodo sono entrambi privati, ma vengono visualizzati in IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Quando si utilizza il `StartCaching` metodo per aggiungere un oggetto dati nella cache di dati, l'oggetto dati non è necessario essere dichiarata con la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo. Tuttavia, l'oggetto dati deve soddisfare determinati requisiti da aggiungere alla cache di dati. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Per memorizzare nella cache a livello di codice di un oggetto dati  
  
1.  Dichiarare l'oggetto dati a livello di classe, non all'interno di un metodo. Questo esempio si presuppone che si sta dichiarando un <xref:System.Data.DataSet> denominato `dataSet1` che si desidera memorizzare nella cache a livello di codice.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Creare un'istanza dell'oggetto dati e quindi chiamare il `StartCaching` metodo dell'istanza di documento o foglio di lavoro e passare il nome dell'oggetto dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>Per interrompere la memorizzazione nella cache un oggetto dati  
  
1.  Chiamare il `StopCaching` metodo dell'istanza di documento o foglio di lavoro e passare il nome dell'oggetto dati. In questo esempio si presuppone un <xref:System.Data.DataSet> denominato `dataSet1` che si desidera interrompere la memorizzazione nella cache.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Non chiamare `StopCaching` dal gestore eventi per il `Shutdown` evento di un documento o foglio di lavoro. Una volta il `Shutdown` evento viene generato, è troppo tardi per modificare la cache dei dati. Per ulteriori informazioni sul `Shutdown` eventi, vedere [eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La memorizzazione nella cache di dati](../vsto/caching-data.md)   
 [Procedura: memorizzare nella Cache di dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: memorizzare nella Cache i dati in un documento protetto da Password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [L'accesso ai dati dei documenti sul Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvataggio di dati](/visualstudio/data-tools/saving-data)  
  
  