---
title: Localizzazione di soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86ffb2795d5e2a9b9583360146c4bb1d2556b9a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-sharepoint-solutions"></a>Localizzazione di soluzioni SharePoint
  Il processo di preparazione delle applicazioni in modo che possono essere utilizzati in tutto il mondo è noto come localizzazione. Localizzazione è conversione di risorse a una lingua specifica. Per ulteriori informazioni, vedere [globalizzazione e localizzazione di applicazioni](/visualstudio/ide/globalizing-and-localizing-applications). In questo argomento viene fornita una panoramica su come localizzare una soluzione di SharePoint.  
  
 Per localizzare una soluzione, si rimuove stringhe hardcoded dal codice ed estrarle in file di risorse. Un file di risorse è un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-basato su file con estensione resx. Il file di risorse contiene le versioni tradotte delle stringhe utilizzate nella soluzione. Per ulteriori informazioni, vedere [risorse nelle applicazioni](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Aggiungere solo le risorse di stringa ai file di risorse di soluzione SharePoint. Sebbene l'Editor risorse permette di aggiungere le risorse non di tipo stringa, le risorse non di tipo stringa non vengono distribuite in SharePoint.  
  
## <a name="resource-files"></a>File di risorse  
 Esistono tre tipi di file di risorse: impostazione predefinita, indipendente dalla lingua e specifico della lingua.  
  
|Tipo di File di risorse|Descrizione|  
|------------------------|-----------------|  
|Impostazione predefinita|Noto anche come risorse di fallback, file di risorse predefiniti contengono stringhe localizzate per le impostazioni cultura predefinite, ad esempio inglese. Vengono utilizzati se non viene trovati alcun file di risorse localizzati per la lingua specificata. Risorse predefinite non dispone di file separati, si trovano nell'assembly principale dell'applicazione.|  
|Indipendente dal linguaggio|Un file di risorse contenente stringhe localizzate per una lingua, ma non una lingua specifica. Ad esempio, "fr" per il francese.|  
|Specifica del linguaggio|Un file di risorse contenente stringhe localizzate per una lingua e impostazioni cultura. Ad esempio, "fr-CA" per il francese canadese.|  
  
 Per ulteriori informazioni, vedere [organizzazione gerarchica di risorse per la localizzazione](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Per specificare i file di risorse predefiniti in progetti di SharePoint che si sviluppano in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], scegliere **lingua (paese invariante)** nell'elenco delle impostazioni cultura di **Aggiungi risorsa** nella finestra di dialogo quando si aggiungere un file di risorse.  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>Localizzazione di soluzioni di SharePoint di Visual Studio  
 Quando si localizza una soluzione, è necessario considerare tutte le informazioni testuali che consente di visualizzare la soluzione per gli utenti. Messaggi informativi, messaggi di errore e [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] stringhe devono essere convertite e inserire le traduzioni nei file di risorse.  
  
 Ogni stringa in un file di risorse dispone di un identificatore univoco. Utilizzare lo stesso identificatore per la stringa tradotta in ogni file di risorse. Se, ad esempio "String1" è l'identificatore per la prima stringa nel file di risorse predefinito, utilizzare lo stesso identificatore per la prima stringa nei file di risorse specifiche della lingua.  
  
 Esistono tre aree in genere localizzate in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazioni di SharePoint: markup delle pagine ASPX e codice. Ai fini dell'illustrazione, le sezioni seguenti si supponga di che disporre di una soluzione di SharePoint che si desidera localizzare in tedesco e giapponese. La lingua predefinita è l'inglese.  
  
### <a name="localizing-features"></a>Localizzazione di funzionalità  
 Per localizzare una funzionalità, è necessario sostituire il titolo hardcoded e la descrizione della funzionalità con un'espressione che fa riferimento il titolo tradotta e la stringa nel file di risorse localizzate. Si apporta questa modifica nel **Progettazione funzionalità** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md).  
  
 Per localizzare la funzionalità inglese in tedesco e giapponese, aggiungere tre elementi di progetto di File di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. I file di risorse di funzionalità non possono essere utilizzati per localizzare il markup ASPX o codice. sono necessari per i file di risorse separati.  
  
 Dopo aver creato la funzionalità file di risorse, aggiungere le stringhe tradotte per loro. Accedere alle stringhe localizzate con un'espressione nel formato seguente:  
  
```  
$Resources:String ID  
```  
  
 Le risorse di funzionalità [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono sempre denominato risorse. Se si seleziona una lingua diversa dall'inglese, quindi le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] viene aggiunto al nome del file di risorse. Ad esempio, se si aggiunge un file di risorse di funzionalità di lingua invariante (impostazione predefinita), bensì Resources. resx. Se si aggiunge una risorsa di funzionalità specifiche della lingua, selezionare una lingua giapponese (Giappone), il file è denominato ja-JP. Nomi di file di risorse di funzionalità vengono assegnati automaticamente e non possono essere modificati.  
  
 L'ambito delle risorse di funzionalità è locale rispetto alla funzionalità a che vengono aggiunti. Per creare le risorse che possono essere utilizzate da qualsiasi file di funzionalità o elementi nella soluzione, aggiungere un **File di risorse globali** elemento di progetto anziché un File di risorse di funzionalità. Il **File di risorse globali** elemento di progetto si trova nella **2010** cartella **SharePoint** nel **Aggiungi nuovo elemento** la finestra di dialogo. Distribuire i file di risorse globali nella cartella \Resources della cartella radice di SharePoint.  
  
### <a name="localizing-aspx-page-markup"></a>Localizzazione di Markup della pagina ASPX  
 Per localizzare [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine, aggiungere tre elementi di progetto di File di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. Se non si dispone di localizzare il codice oltre il markup, è invece possibile aggiungere file di risorse globali.  
  
 Specificare un nome per il file di risorse di lingua predefinita. Assegnare i file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ad esempio, MyAppResources.de-de per il tedesco e MyAppResources. ja-JP per il giapponese.  
  
 Impostare il **tipo di distribuzione** proprietà di ogni file di risorse per **AppGlobalResource**. In questo modo i file di risorse per la cartella App_GlobalResources, in cui sono disponibili per tutte le pagine ASPX e controlli nella soluzione. Si trova nella cartella App_GlobalResources in C:\inetpub\wwwroot\wss\VirtualDirectories\\< numero porta\>\App_GlobalResources.  
  
> [!NOTE]  
>  Se si utilizzano file di risorse non globali, spostarli nella cartella dell'elemento di progetto per abilitare il tipo di distribuzione e altre proprietà specifiche di SharePoint.  
  
 File di risorse markup ASPX anche utilizzabile per localizzare il codice. Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare l'azione di compilazione impostazione della proprietà di ogni file come risorsa incorporata per la risorsa per la compilazione in un assembly satellite. Tuttavia, se si utilizza i file di risorse solo per localizzare il markup, è facoltativamente possibile modificare l'azione di compilazione al contenuto per impedire che il file viene compilato nell'assembly principale dell'applicazione.  
  
 Sostituire tutte le stringhe hardcoded proprietà nel markup ASPX pagine e controlli con un'espressione nel formato seguente:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Per ASPX come testo, utilizzare un'espressione nel formato seguente:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Per ulteriori informazioni, vedere [procedura: localizzare il Markup ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localizing-code"></a>Localizzazione di codice  
 Oltre alle stringhe di funzionalità di localizzazione e [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] markup, è anche necessario localizzare le stringhe di messaggio ed errore che vengono visualizzati nel codice della soluzione. Localizzati informativi e i messaggi di errore sono contenuti negli assembly satellite. Gli assembly satellite contengono le stringhe che sono visibili agli utenti, ad esempio [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] messaggi di testo e di output come eccezioni.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il modello hub e spoke di .NET Framework standard. L'hub o un assembly di programma principale, contiene le risorse di lingua predefinita. Spoke, o gli assembly satellite, contengono le risorse specifiche della lingua. Per altre informazioni, vedere [Creazione del pacchetto e distribuzione delle risorse](http://go.microsoft.com/fwlink/?LinkId=179280). Gli assembly satellite vengono compilati i file di risorse (resx). Quando si aggiungono file di risorse specifiche della lingua per il progetto e il pacchetto della soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila i file di risorse in assembly satellite denominato *nome progetto*. Resources.  
  
 Come con markup ASPX, localizzare il codice dell'applicazione SharePoint tramite l'aggiunta di elementi di progetto di File di risorse separati al progetto. uno per la lingua predefinita e uno per ogni lingua localizzata. Tuttavia, come indicato in precedenza, se si dispone già di file di risorse per localizzare il markup ASPX, è possibile riutilizzarli per localizzare il codice. Se si desidera creare file di risorse, assegnare un nome di propria scelta con estensione resx il file di risorse di lingua predefinita. Nome file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Impostare la proprietà azione di compilazione di ogni file di risorse per la risorsa incorporata per consentire la creazione di assembly di risorse satellite.  
  
 Per creare gli assembly satellite, compilare il progetto e quindi aggiungere i file come assembly aggiuntivi tramite il **avanzate** scheda della finestra di **Progettazione pacchetti**. Quando si aggiungono gli assembly, anteporre le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] cartella al percorso, ad esempio de-DE\\*nome di elemento di progetto*. Resources. In questo modo il pacchetto contenga i file che hanno lo stesso nome.  
  
 Nel codice, sostituire le stringhe hardcoded con chiamate al <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metodo utilizzando la sintassi seguente:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Per ulteriori informazioni, vedere [procedura: localizzare codice](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localizzazione di codice di Web Part  
 Web part includono una funzionalità dell'editor di proprietà personalizzata che include gli attributi di codice che utilizzano le stringhe hardcoded, ad esempio WebDisplayName, Category e WebDescription. Per sostituire i valori di stringa per questi attributi, creare una classe separata che deriva dalla classe dell'attributo. In tali classi, impostare la proprietà dell'attributo. La proprietà dell'attributo dipende dalla classe base. Ad esempio, la proprietà di attributo WebDisplayName è DisplayNameValue e la proprietà dell'attributo WebDescription è DescriptionValue.  
  
 Nella classe derivata, fare riferimento all'ID di stringa da file di risorse e l'oggetto ResourceManager per ottenere il valore localizzato per l'ID di stringa. Restituisce questo valore per l'attributo di editor di proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: localizzare il Markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)   
 [Procedura: aggiungere un File di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  