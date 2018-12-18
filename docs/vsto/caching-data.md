---
title: La memorizzazione nella cache dati | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>Memorizzazione di dati nella cache
  È possibile memorizzare nella cache di oggetti dati in una personalizzazione a livello di documento in modo che i dati sono accessibili, offline o senza l'apertura di Microsoft Office Word o Microsoft Office Excel. Per memorizzare nella cache un oggetto, l'oggetto deve avere un tipo di dati che soddisfano determinati requisiti. Molti tipi di dati comuni in .NET Framework soddisfano questi requisiti, compresi <xref:System.String>, <xref:System.Data.DataSet>, e <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Esistono due modi per aggiungere un oggetto alla cache di dati:  
  
-   Per aggiungere un oggetto alla cache di dati durante la compilazione della soluzione, applicare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo alla dichiarazione dell'oggetto. Per ulteriori informazioni, vedere [procedura: memorizzare i dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Per aggiungere a livello di codice un oggetto alla cache di dati in fase di esecuzione, utilizzare il `StartCaching` elemento metodo di un host, ad esempio il `ThisDocument` o `ThisWorkbook` classi. Per ulteriori informazioni, vedere [procedura: memorizzare nella Cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Dopo aver aggiunto un oggetto alla cache di dati, è possibile accedere e modificare i dati memorizzati nella cache senza avviare Word o Excel. Per altre informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Requisiti per gli oggetti dati da memorizzare nella cache  
 Per memorizzare nella cache un oggetto dati nella soluzione, l'oggetto deve soddisfare questi requisiti:  
  
-   Essere un campo pubblico in lettura/scrittura o una proprietà di un elemento host, ad esempio il `ThisDocument` o `ThisWorkbook` classi.  
  
-   Non è un indicizzatore né altre proprietà con parametri.  
  
 Inoltre, l'oggetto dati deve essere serializzabile dal <xref:System.Xml.Serialization.XmlSerializer> (classe), ovvero il tipo dell'oggetto deve avere le seguenti caratteristiche:  
  
-   Essere un tipo pubblico.  
  
-   Ha un costruttore pubblico senza parametri.  
  
-   Esegue il codice che richiede privilegi di sicurezza aggiuntive.  
  
-   Esporre solo proprietà read/write pubblico (altre proprietà verrà ignorata).  
  
-   Non esporre le matrici multidimensionali (matrici annidate sono accettate).  
  
-   Interfacce non restituite dalla proprietà e campi.  
  
-   Non implementare <xref:System.Collections.IDictionary> se una raccolta.  
  
 Quando si memorizza nella cache un oggetto dati, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML che viene archiviata in un *parte XML personalizzata* nel documento. Per altre informazioni, vedere [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limiti delle dimensioni dei dati memorizzati nella cache  
 Vi sono alcuni limiti alla quantità totale di dati che è possibile aggiungere alla cache di dati in un documento e per le dimensioni di qualsiasi singolo oggetto nella cache dei dati. Se si superano questi limiti, l'applicazione verifichi la chiusura imprevista quando i dati vengono salvati nella cache di dati.  
  
 Per evitare questi limiti, seguire queste linee guida:  
  
-   Non aggiungere qualsiasi oggetto maggiore di 10 MB per la cache dei dati.  
  
-   Non aggiungere più di 100 MB di dati totali alla cache di dati in un singolo documento.  
  
 Questi sono i valori approssimativi. I limiti esatti dipendono da diversi fattori, tra la RAM disponibile e il numero di processi in esecuzione.  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>Controllare il comportamento di oggetti memorizzati nella cache  
 Per ottenere un maggiore controllo sul comportamento di un oggetto memorizzato nella cache, è possibile implementare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia del tipo di oggetto memorizzato nella cache. Ad esempio, è possibile implementare questa interfaccia se si desidera controllare come l'utente riceve una notifica quando l'oggetto è stato modificato. Per esempi di codice che illustrano come implementare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, vedere il `ControlCollection` classe nell'esempio di controlli dinamici di Excel di esempio di controlli dinamici di Word in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>Rendere persistenti le modifiche ai dati memorizzati nella cache di documenti protetti da Password  
 Se si memorizza nella cache gli oggetti dati in un documento protetto con una password, le modifiche ai dati memorizzati nella cache non vengono salvate. È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi. Eseguire l'override di questi metodi per rimuovere temporaneamente la protezione quando il documento viene salvato e quindi riapplicare la protezione dopo il salvataggio operazione è stata completata.  
  
 Per ulteriori informazioni, vedere [procedura: memorizzare i dati in un documento Password-Protected](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>Come evitare la perdita di dati durante l'aggiunta di valori Null per la Cache dei dati  
 Quando si aggiungono oggetti alla cache di dati, tutti gli oggetti memorizzati nella cache devono essere inizializzati su non**null** valore prima che il documento viene salvato e chiuso. Se qualsiasi oggetto memorizzato nella cache è un **null** valore quando il documento viene salvato e chiuso, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuoverà automaticamente tutti gli oggetti memorizzati nella cache dalla cache dei dati.  
  
 Se si aggiunge un oggetto con un **null** valore per la cache dei dati tramite il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo in fase di progettazione, è possibile utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per inizializzare i dati memorizzati nella cache oggetti prima che il documento viene aperto. Ciò è utile se si desidera inizializzare i dati memorizzati nella cache in un server senza Word o Excel, prima che il documento viene aperto da un utente finale. Per altre informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: memorizzare nella Cache di dati per l'utilizzo Offline o in un Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: memorizzare nella Cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Procedura: memorizzare nella Cache i dati in un documento protetto da Password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Procedura dettagliata: creazione di una relazione master/dettaglio mediante un set di dati memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  