---
title: Schemi e dati nelle personalizzazioni a livello di documento XML | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8be23f82d03faa30cf8a6e180edb741c5f60814
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML Schema e dati nelle personalizzazioni a livello di documento
  **Importante** le informazioni in questo argomento relative a Microsoft Word sono presentato in modo esclusivo per il vantaggio e uso di singoli utenti e organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che utilizzano o lo sviluppo programmi che vengono eseguiti in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di una funzionalità specifica relativi a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word potrebbero non essere lette o utilizzate dal singoli individui o organizzazioni negli Stati Uniti o relativi territori, che utilizza o lo sviluppo di programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti con licenza prima di tale data o acquistati e concesso in licenza di fuori degli Stati Uniti.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel e Microsoft Office Word consentono di eseguire il mapping di schemi per i documenti. Questa funzionalità può semplificare l'importazione ed esportazione di dati XML da e verso il documento.  
  
 Visual Studio vengono esposti eseguito il mapping di elementi dello schema nelle personalizzazioni a livello di documento come controlli nel modello di programmazione. Per Excel, Visual Studio aggiunge il supporto per i controlli di associazione ai dati nel database, servizi Web e oggetti. Per Word ed Excel, Visual Studio aggiunge il supporto per i riquadri azioni, che può essere usato con un documento di stato eseguito il mapping dello schema per creare un'esperienza avanzata per utenti finali per le soluzioni. Per altre informazioni, vedere [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  È possibile utilizzare schemi XML multipart nelle soluzioni Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Oggetti creati quando gli schemi sono collegati a cartelle di lavoro di Excel  
 Quando si allega uno schema in una cartella di lavoro, Visual Studio automaticamente crea più oggetti e li aggiunge al progetto. Questi oggetti non devono essere eliminati utilizzando gli strumenti di Visual Studio, perché sono gestiti da Excel. Per eliminarli, rimuovere gli elementi mappati dal foglio di lavoro o scollegare lo schema utilizzando gli strumenti di Excel.  
  
 Esistono due oggetti principali:  
  
-   Schema XML (file con estensione XSD). Per ogni schema nella cartella di lavoro, Visual Studio aggiunge uno schema al progetto. Viene visualizzato come elemento di progetto con estensione XSD in **Esplora**.  
  
-   Una classe <xref:System.Data.DataSet> tipizzata. Questa classe viene creata in base a schema. Questa classe dataset è visibile in **Visualizzazione classi**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Oggetti creati quando viene eseguito il mapping di elementi dello Schema a fogli di lavoro di Excel  
 Quando si esegue il mapping di un elemento dello schema dal **origine XML** riquadro attività a un foglio di lavoro, Visual Studio automaticamente crea più oggetti e li aggiunge al progetto:  
  
-   Controlli. Per ogni oggetto mappato nella cartella di lavoro, un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo (per gli elementi dello schema non ripetuti) o un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo (per gli elementi dello schema ripetuti) viene creato nel modello di programmazione. Il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo può essere eliminato solo eliminando il mapping e gli oggetti mappati dalla cartella di lavoro. Per ulteriori informazioni sui controlli, vedere [elementi Host e Cenni preliminari sui controlli Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Quando si crea un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eseguendo il mapping di un elemento dello schema non ripetuto nel foglio di lavoro un <xref:System.Windows.Forms.BindingSource> viene creato e <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è associato al <xref:System.Windows.Forms.BindingSource>. È necessario associare il <xref:System.Windows.Forms.BindingSource> a un'istanza dell'origine dati che corrisponde allo schema di cui è stato eseguito il mapping al documento, ad esempio un'istanza dell'oggetto tipizzato <xref:System.Data.DataSet> classe che è stato creato. Creare l'associazione impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> le proprietà che vengono esposte nel **proprietà** finestra.  
  
    > [!NOTE]  
    >  Il <xref:System.Windows.Forms.BindingSource> non viene creata per <xref:Microsoft.Office.Tools.Excel.ListObject> oggetti. È necessario associare manualmente il <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> le proprietà di **proprietà** finestra.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>La finestra Origini dati di Visual Studio e schemi mappati di Office  
 Entrambe le funzionalità di schema mappati di Office e di Visual Studio **origini dati** finestra consentono di presentare i dati in un foglio di lavoro di Excel per report o la modifica. In entrambi i casi è possibile trascinare gli elementi di dati del foglio di lavoro di Excel. Entrambi i metodi di creano controlli associati a dati mediante un <xref:System.Windows.Forms.BindingSource> a un'origine dati, ad esempio un <xref:System.Data.DataSet> o un servizio Web.  
  
> [!NOTE]  
>  Quando si esegue il mapping di un elemento ripetuto dello schema a un foglio di lavoro, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject>. Il <xref:Microsoft.Office.Tools.Excel.ListObject> non viene associato automaticamente ai dati tramite il <xref:System.Windows.Forms.BindingSource>. È necessario associare manualmente il <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> le proprietà di **proprietà** finestra.  
  
 Nella tabella seguente vengono illustrate alcune delle differenze tra i due metodi.  
  
|Schema XML|Finestra Origini dati|  
|----------------|-------------------------|  
|Usa l'interfaccia di Office.|Usa **origini dati** finestra in Visual Studio.|  
|Abilita le funzionalità incorporate di Office per importare ed esportare dati da file XML.|È necessario consentire l'importazione e la funzionalità di esportazione a livello di codice.|  
|È necessario scrivere codice per inserire i controlli generati i dati.|I controlli aggiunti dal **origini dati** finestra dispone di codice generato automaticamente per compilare i campi, insieme a stringhe di connessione necessarie quando si utilizzano server di database.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamento quando gli schemi sono collegati ai documenti di Word  
 Oggetti dati non vengono creati quando si collega uno schema a un documento di Word che viene utilizzato in un progetto di Office a livello di documento. Tuttavia, quando si esegue il mapping di un elemento dello schema al documento, vengono creati controlli. Il tipo di controllo dipende dal tipo di elemento è mappato. gli elementi ripetitivi generano <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli e gli elementi non ripetuti generare <xref:Microsoft.Office.Tools.Word.XMLNode> controlli. Per ulteriori informazioni, vedere [XMLNodes (controllo)](../vsto/xmlnodes-control.md) e [XMLNode (controllo)](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Distribuzione di soluzioni che includono schemi XML  
 È necessario creare un programma di installazione per distribuire una soluzione che utilizza uno schema XML che viene eseguito il mapping a un documento. Il programma di installazione deve registrare lo schema nella raccolta di schemi nel computer dell'utente. Se non si registra lo schema, la soluzione funzionerà comunque perché Word consente di generare uno schema temporaneo basato sugli elementi inclusi nel documento quando l'utente viene aperto. Tuttavia, l'utente non sarà in grado di eseguire la convalida o salvare lo schema utilizzato per creare il progetto. Per ulteriori informazioni sui programmi di installazione, vedere [distribuzione di applicazioni, servizi e componenti](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 È anche possibile aggiungere codice al progetto per controllare se lo schema nella raccolta e registrato. In caso contrario, è possibile informare l'utente.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  