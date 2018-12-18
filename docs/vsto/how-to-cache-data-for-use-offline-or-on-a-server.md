---
title: 'Procedura: memorizzare nella Cache di dati per l''utilizzo Offline o in un Server | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44130744af5d09e8582e2589bcefb7aca11b5ce2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server
  È possibile contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. Ciò consente inoltre per i dati del documento deve essere modificato da altro codice quando il documento viene archiviato in un server.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile contrassegnare un elemento di dati da memorizzare nella cache quando l'elemento di dati viene dichiarato nel codice o, se si utilizza un <xref:System.Data.DataSet>, impostando una proprietà **proprietà** finestra. Se si memorizza nella cache un elemento di dati che non è un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>, assicurarsi che vengano soddisfatti i criteri per la cache del documento. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Set di dati creati utilizzando Visual Basic che sono contrassegnati come **memorizzata nella cache** e **WithEvents** (inclusi i set di dati trascinati dal **origini dati** finestra o **Casella degli strumenti** che dispongono di **CacheInDocument** proprietà impostata su **True**) dispone di un carattere di sottolineatura come prefisso per i relativi nomi nella cache. Ad esempio, se si crea un set di dati e denominarlo **clienti**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nome sarà **Customers** nella cache. Quando si utilizza <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere a questo elemento memorizzato nella cache, è necessario specificare **Customers** anziché **clienti**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Per memorizzare i dati nel documento tramite codice  
  
1.  Dichiarare un campo pubblico o una proprietà per l'elemento di dati come un membro di una classe dell'elemento host del progetto, ad esempio il `ThisDocumen`classe in un progetto di Word o `ThisWorkbook` classe in un progetto di Excel.  
  
2.  Applicare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo per il membro per contrassegnare l'elemento di dati da archiviare nella cache di dati del documento. Nell'esempio seguente viene applicato questo attributo a una dichiarazione di campo per un <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Aggiungere il codice per creare un'istanza dell'elemento di dati e, se applicabile, caricarlo dal database.  
  
     L'elemento di dati viene caricato solo quando viene creato inizialmente; Successivamente, la cache rimanga nel documento mentre è necessario scrivere codice per eseguire l'aggiornamento.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Per memorizzare nella cache un set di dati nel documento tramite la finestra proprietà  
  
1.  Aggiungere il set di dati al progetto utilizzando gli strumenti di progettazione di Visual Studio, ad esempio, aggiungendo un'origine dati al progetto mediante il **origini dati** finestra.  
  
2.  Creare un'istanza del set di dati se non si è già presente e selezionare l'istanza nella finestra di progettazione.  
  
3.  Nel **proprietà** finestra, impostare il **CacheInDocument** proprietà **True**.  
  
     Per ulteriori informazioni, vedere [proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).  
  
4.  Nel **proprietà** finestra, impostare il **modificatori** proprietà **pubblica** (per impostazione predefinita è **interno**).  
  
## <a name="see-also"></a>Vedere anche  
 [La memorizzazione nella cache di dati](../vsto/caching-data.md)   
 [Procedura: memorizzare nella Cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Procedura: memorizzare nella Cache i dati in un documento protetto da Password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [L'accesso ai dati nei documenti nel Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvataggio di dati](/visualstudio/data-tools/saving-data)  
  
  