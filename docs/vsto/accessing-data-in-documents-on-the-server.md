---
title: L'accesso ai dati nei documenti nel Server | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d1831649c36249f4858dc5bd52ea90b4fd938eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-data-in-documents-on-the-server"></a>Accesso ai dati dei documenti sul server
  È possibile programmare i dati in una personalizzazione a livello di documento senza la necessità di utilizzare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel. Ciò significa che è possibile accedere ai dati contenuti in un documento in un server che non dispone di Word o Excel installato. Esempio di codice in un server (ad esempio, in un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina) possono personalizzare i dati in un documento e inviare il documento personalizzato a un utente finale. Quando l'utente finale apre il documento, il codice di associazione di dati nell'assembly della soluzione Associa dati personalizzati nel documento. Questo è possibile perché i dati nel documento sono separatati dall'interfaccia utente. Per ulteriori informazioni, vedere [dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="caching-data-for-use-on-a-server"></a>Memorizzazione nella cache i dati per l'utilizzo in un Server  
 Per memorizzare nella cache un oggetto dati in un documento, contrassegnarlo con il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> o di attributo in fase di progettazione oppure utilizzare il `StartCaching` metodo di un elemento host in fase di esecuzione. Quando si memorizza nella cache un oggetto dati in un documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML che viene archiviata nel documento. Gli oggetti devono soddisfare determinati requisiti per essere idoneo per la memorizzazione nella cache. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  

 Il codice lato server è possibile modificare tutti gli oggetti dati nella cache dei dati. Controlli associati a dati memorizzati nella cache istanze sono sincronizzati con l'interfaccia utente, in modo che le modifiche sul lato server effettuate per i dati vengono visualizzate automaticamente quando il documento viene aperto nel client.  

## <a name="accessing-data-in-the-cache"></a>L'accesso ai dati nella Cache  
 È possibile accedere a dati memorizzati nella cache dalle applicazioni all'esterno dell'ufficio, ad esempio da un'applicazione console, un'applicazione Windows Form o una pagina Web. L'applicazione che accede ai dati memorizzati nella cache deve avere l'attendibilità totale; un'applicazione Web con attendibilità parziale non può inserire, recuperare o modificare i dati memorizzati nella cache in un documento di Office.  

 La cache dei dati è accessibile tramite una gerarchia delle raccolte esposte dal <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe:  

-   Il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà restituisce un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, che contiene tutti i dati memorizzati nella cache in una personalizzazione a livello di documento.  

-   Ogni <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene tutti gli oggetti dati memorizzati nella cache definiti all'interno di una singola classe.  

-   Ogni <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> rappresenta un oggetto solo dati memorizzati nella cache.  

 Esempio di codice riportato di seguito viene illustrato come accedere a una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modifying-data-in-the-cache"></a>Modifica dei dati nella Cache  
 Per modificare un oggetto dati memorizzati nella cache, è in genere necessario eseguire i passaggi seguenti:  

1.  Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto. È possibile accedere al codice XML tramite il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> che rappresenta l'oggetto dati memorizzati nella cache.  

2.  Apportare le modifiche a tale copia.  

3.  Serializzare l'oggetto modificato nuovamente nella cache di dati utilizzando una delle opzioni seguenti:  

    -   Se si desidera serializzare automaticamente le modifiche, utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo. Questo metodo Usa il **DiffGram** formato per la serializzazione <xref:System.Data.DataSet>, <xref:System.Data.DataTable>e gli oggetti dataset tipizzati nella cache dei dati. Il **DiffGram** formato garantisce che le modifiche apportate alla cache di dati in un documento non in linea vengono inviate correttamente al server.  

    -   Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati nella cache, è possibile scrivere direttamente il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà. Specificare il **DiffGram** formattare se si utilizza un <xref:System.Data.Common.DataAdapter> per aggiornare un database con le modifiche apportate ai dati in un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o un dataset tipizzato. In caso contrario, il <xref:System.Data.Common.DataAdapter> aggiornerà il database tramite l'aggiunta di nuove righe anziché modificare le righe esistenti.  

### <a name="modifying-data-without-deserializing-the-current-value"></a>Modifica dei dati senza deserializzare il valore corrente  
 In alcuni casi, si potrebbe voler modificare il valore dell'oggetto memorizzato nella cache senza prima deserializzare il valore corrente. Ad esempio, è possibile farlo se si modifica il valore di un oggetto che presenta un tipo semplice, ad esempio una stringa o un numero intero, o se si inizializza un oggetto nella cache <xref:System.Data.DataSet> in un documento in un server. In questi casi, è possibile utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo senza prima deserializzare il valore corrente dell'oggetto memorizzato nella cache.  

 Esempio di codice riportato di seguito viene illustrato come modificare il valore di una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modifying-null-values-in-the-data-cache"></a>Modifica dei valori Null nella Cache dei dati  
 La cache dei dati non archivia gli oggetti che hanno il valore **null** quando il documento viene salvato e chiuso. Questa limitazione ha diverse conseguenze quando si modificano i dati memorizzati nella cache:  

-   Se è impostare qualsiasi oggetto nella cache dei dati per il valore **null**, tutti gli oggetti nella cache dei dati verrà automaticamente impostati su **null** quando il documento viene aperto e verrà cancellata l'intera cache di dati quando il documento viene salvato e chiuso. Vale a dire tutti gli oggetti memorizzati nella cache verranno rimossi dalla cache dei dati e <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> raccolta sarà vuota.  

-   Se si compila una soluzione con **null** oggetti nella cache dei dati e si desidera inizializzare questi oggetti utilizzando il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe prima che il documento viene aperto per la prima volta, è necessario assicurarsi di inizializzare tutti gli oggetti nella cache dei dati. Se si inizializza solo alcuni degli oggetti, tutti gli oggetti verrà impostati su **null** quando il documento viene aperto e verrà cancellata la cache di dati quando il documento viene salvato e chiuso.  

## <a name="accessing-typed-datasets-in-the-cache"></a>L'accesso a un dataset tipizzati nella Cache  
 Se si desidera accedere ai dati in un dataset tipizzato da una soluzione Office e da un'applicazione all'esterno dell'ufficio, ad esempio un'applicazione Windows Form o un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] progetto, è necessario definire il dataset tipizzato in un assembly separato a cui fa riferimento in entrambi progetti. Se aggiungere a ogni progetto dataset tipizzato utilizzando il **configurazione guidata origine dati** o **Progettazione Dataset**, .NET Framework verranno considerati i due progetti come diversi tipi di dataset tipizzati . Per ulteriori informazioni sulla creazione di dataset tipizzati, vedere [creare e configurare i set di dati in Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Vedere anche  
 [L'accesso ai dati dei documenti sul Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)  
