---
title: La creazione di elementi modelli di progetto e modelli per gli elementi di progetto SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f71352dad7b77b2ce92816e84a7c90ec16710ed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>Creazione di modelli di elemento e di modelli di progetto per gli elementi di progetto SharePoint
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile associare e con un modello di elemento o un modello di progetto in modo che altri sviluppatori possono usare l'elemento del progetto in Visual Studio. È inoltre possibile creare una procedura guidata per il modello.  
  
 Ad esempio, Visual Studio non include un modello di progetto o un modello di elemento per aggiungere un campo a un sito di SharePoint. È possibile definire un tipo di elemento di progetto SharePoint che rappresenta un campo e quindi creare un modello di elemento che altri sviluppatori possono usare per aggiungere l'elemento del campo a un progetto SharePoint. In alternativa, è possibile creare un modello di progetto in modo che gli sviluppatori possono creare un nuovo progetto di SharePoint che contiene l'elemento del campo. In entrambi i casi, è possibile fornire anche una procedura guidata che viene visualizzato quando gli sviluppatori utilizzano il modello. Questa procedura guidata è possibile raccogliere informazioni da parte degli sviluppatori per configurare il nuovo elemento o un progetto.  
  
 Modelli di progetto e modelli di elementi sono file con estensione zip che contiene i file vengono utilizzati da Visual Studio per creare un progetto o un elemento di progetto. Per ulteriori informazioni sulle nozioni di base di modelli di progetto e modelli di elemento, vedere [creazione Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates).  
  
##  <a name="creatingitemtemplates"></a> Creazione di modelli di elementi  
 Quando si crea un modello di elemento per un elemento di progetto SharePoint, esistono alcuni file che sono sempre necessari e file facoltativi che potrebbero essere utilizzati da determinati tipi di elementi di progetto. Per una procedura dettagliata viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di elemento per essa, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Nella tabella seguente sono elencati i file necessari per creare un modello di elemento per un elemento di progetto SharePoint.  
  
|File obbligatorio|Descrizione|  
|-------------------|-----------------|  
|Un file con estensione spdata|Si tratta di un file XML che specifica il contenuto e il comportamento predefinito dell'elemento del progetto. Questo file deve essere incluso nel modello di elemento. Per ulteriori informazioni sul contenuto dei file spdata, vedere [riferimenti dello Schema di elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Un file. vstemplate.|Questo file fornisce le informazioni necessarie per visualizzare il modello in Visual Studio il **Aggiungi nuovo elemento** la finestra di dialogo e creare un elemento di progetto dal modello. Questo file deve essere incluso nel modello di elemento. Per ulteriori informazioni, vedere [metadati file modello di Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia.|Questo assembly definisce il comportamento di runtime dell'elemento del progetto. Questo assembly deve essere incluso nel pacchetto VSIX con il modello di elemento. Per ulteriori informazioni, vedere [tipi di elemento di definizione personalizzato SharePoint progetto](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 Nella tabella seguente sono elencati alcuni dei più comuni file facoltativi che possono essere incluso nel modello di elemento. Alcuni tipi di elementi di progetto potrebbero richiedere altri file non elencate di seguito.  
  
|File facoltativo|Descrizione|  
|-------------------|-----------------|  
|Elements|Oggetto *funzionalità elemento* file. Questo file definisce l'interfaccia utente e il comportamento di personalizzazione creata dall'elemento del progetto. Ogni tipo di personalizzazione, ad esempio le istanze di elenco, tipi di contenuto o le azioni personalizzate, ha uno schema diverso che definisce il contenuto di questo file. Per ulteriori informazioni, vedere [blocco predefinito: funzionalità](http://go.microsoft.com/fwlink/?LinkId=169183) e [funzionalità schemi](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.Xml|Il file di schema per le definizioni di elenco. Per ulteriori informazioni, vedere [blocco predefinito: elenchi e raccolte documenti](http://go.microsoft.com/fwlink/?LinkId=177792) e [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|con estensione WebPart|Oggetto *definizione della Web Part* file. Questo file contiene le impostazioni delle proprietà per una Web Part. Per ulteriori informazioni, vedere [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|con estensione ascx|Un file di controllo utente ASP.NET. Questo file definisce l'interfaccia utente di una Web Part visiva.|  
|.aspx|Un file della pagina ASP.NET. Questo file contiene codice XML che definisce una pagina dell'applicazione.|  
|file con estensione cs o vb|Questi file di codice definiscono il comportamento delle personalizzazioni di SharePoint che dispone di un modello di programmazione che è possibile accedere da Visual c# o Visual Basic (codice), ad esempio le pagine dell'applicazione, Web part e flussi di lavoro.|  
  
## <a name="creating-project-templates"></a>Creazione di modelli di progetto  
 Quando si crea un modello di progetto SharePoint, esistono alcuni file che sono sempre file obbligatori e facoltativi che potrebbero essere utilizzati da determinati tipi di progetti. In genere, i progetti SharePoint includono almeno un elemento di progetto SharePoint. Tuttavia, non necessari. Ad esempio, è possibile definire un modello di progetto SharePoint che dovrà essere utilizzato solo per distribuire le soluzioni SharePoint create in altri progetti.  
  
 Per una procedura dettagliata viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di progetto per essa, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Nella tabella seguente sono elencati i file che devono essere inclusi in un modello di progetto SharePoint.  
  
|File obbligatorio|Descrizione|  
|-------------------|-----------------|  
|Un file con estensione vstemplate|Questo file fornisce le informazioni necessarie per visualizzare il modello in Visual Studio il **nuovo progetto** la finestra di dialogo e creare un progetto dal modello. Per ulteriori informazioni, vedere [metadati file modello di Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un file con estensione csproj o vbproj|Si tratta del file di progetto. Definisce il contenuto e le impostazioni di configurazione del progetto.|  
|Package. package|Questo file definisce il pacchetto di distribuzione per il progetto. Quando si utilizza la finestra di progettazione del pacchetto per personalizzare il pacchetto della soluzione per il progetto, Visual Studio archivia i dati sul pacchetto della soluzione in questo file.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, si consiglia di includere solo la minima richiesta contenuto nel file package. package e configurare il pacchetto della soluzione tramite l'API di <xref:Microsoft.VisualStudio.SharePoint.Packages> spazio dei nomi in un'estensione associato al modello di progetto. In questo caso, il modello di progetto è protetto da modifiche future della struttura del file package. package. Per un esempio che illustra come creare un file package. package con solo il requisito minimo del contenuto, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente il file package. package, è possibile verificare il contenuto mediante lo schema in % programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd.|  
|Package.Template.xml|Questo file costituisce la base per il file manifesto (manifest.xml) della soluzione per il pacchetto della soluzione SharePoint (con estensione wsp) generato dal progetto. Se si desidera specificare un comportamento che non può essere modificato dagli utenti del tipo di progetto, è possibile aggiungere contenuto al file. Per ulteriori informazioni, vedere [blocco predefinito: soluzioni](http://go.microsoft.com/fwlink/?LinkId=169186) e [Schema soluzione](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il contenuto del file package. package e i file Package.Template.xml nella soluzione del file manifesto. Per ulteriori informazioni sulla compilazione di pacchetti della soluzione, vedere [procedura: creare un pacchetto della soluzione SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 Nella tabella seguente elenca i file facoltativi che possono essere incluso nel modello di progetto.  
  
|File facoltativo|Descrizione|  
|-------------------|-----------------|  
|SharePoint (elementi di progetto)|È possibile includere uno o più file di estensione spdata che definiscono i tipi di elemento di progetto SharePoint. Ogni file con estensione spdata deve avere un corrispondente <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione in un assembly di estensione che è incluso nel pacchetto con il modello di progetto VSIX. Per ulteriori informazioni, vedere [creazione di modelli di elemento](#creatingitemtemplates).<br /><br /> In genere, i progetti SharePoint includono almeno un elemento di progetto SharePoint. Tuttavia, non necessari.|  
|*featureName*feature|Questo file definisce una funzionalità di SharePoint che viene utilizzato per raggruppare diversi elementi di progetto per la distribuzione. Quando si utilizza la finestra di progettazione di funzionalità per personalizzare una funzionalità nel progetto, Visual Studio archivia i dati sulla funzionalità in questo file. Se si desidera raggruppare gli elementi del progetto in diverse funzionalità, è possibile includere più file con estensione feature.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto richiesto minimo in ogni file con estensione feature, e configurare le funzionalità tramite l'API di <xref:Microsoft.VisualStudio.SharePoint.Features> dello spazio dei nomi in un'estensione che è associata il modello di progetto. In questo caso, il modello di progetto è protetto da modifiche future alla struttura del file con estensione feature. Per un esempio che illustra come creare un file con estensione feature con solo il requisito minimo del contenuto, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente un file con estensione feature, è possibile verificare il contenuto mediante lo schema in % programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd.|  
|*featureName*. Template. Xml|Questo file costituisce la base per il file manifesto di funzionalità (feature) per ogni funzionalità che viene generato dal progetto. Se si desidera specificare un comportamento che non può essere modificato dagli utenti del tipo di progetto, è possibile aggiungere contenuto al file. Per ulteriori informazioni, vedere [blocco predefinito: funzionalità](http://go.microsoft.com/fwlink/?LinkId=169183) e [feature](http://go.microsoft.com/fwlink/?LinkId=177795) file.<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il contenuto di ogni coppia di *featureName*file con estensione feature e *featureName*. Template file in un file manifesto di funzionalità. Per ulteriori informazioni sulla compilazione di pacchetti della soluzione, vedere [procedura: creare un pacchetto della soluzione SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## <a name="creating-wizards-for-item-templates-and-project-templates"></a>Creazione di procedure guidate per i modelli di elemento e i modelli di progetto  
 Dopo aver definito un tipo di elemento di progetto SharePoint e associarlo a un elemento o un progetto di modello, è possibile creare anche una procedura guidata. La procedura guidata viene visualizzato quando uno sviluppatore utilizza il modello di elemento per aggiungere l'elemento del progetto SharePoint a un progetto o quando uno sviluppatore utilizza il modello di progetto per creare un nuovo progetto che contiene l'elemento di progetto SharePoint. La procedura guidata può essere utilizzata per raccogliere informazioni da sviluppatori e inizializzare il nuovo elemento di progetto SharePoint.  
  
 Per procedure dettagliate che illustrano come creare procedure guidate per i modelli di elemento e i modelli di progetto, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [procedura dettagliata: creazione di un sito Elemento di progetto colonna con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Creazione di modelli di progetti e di elementi](/visualstudio/ide/creating-project-and-item-templates)  
  
  