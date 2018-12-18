---
title: Fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adc98932391e726e1704ebe88ec0a9120f7bb678
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto
  Tutti gli elementi di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dispongono di proprietà che è possibile utilizzare per fornire dati aggiuntivi quando il progetto viene distribuito in SharePoint. Di seguito sono riportate le proprietà:  
  
-   Proprietà funzionalità  
  
-   Ricevitori di funzionalità  
  
-   Riferimenti all'output del progetto  
  
-   Voci di controllo sicure  
  
 Queste proprietà vengono visualizzate nel **proprietà** finestra.  
  
## <a name="feature-properties"></a>Proprietà funzionalità  
 Utilizzare il **le proprietà della funzionalità** proprietà per specificare i dati che utilizza la funzionalità. Dati delle proprietà della funzionalità è un set di valori (archiviati come coppie chiave/valore) incluso in una funzionalità al momento della distribuzione in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice.  
  
 Quando si aggiunge un valore della proprietà di funzionalità a un elemento di progetto, il valore viene aggiunto come elemento nel manifesto della funzionalità dell'elemento. In un progetto di modello di integrazione applicativa dei dati (BDC), ad esempio, la proprietà della funzionalità ModelFileName viene visualizzato come:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Dopo aver impostato un valore della proprietà di funzionalità, aggiungerlo come elemento FeatureProperty nel file con estensione spdata del progetto. Per informazioni sull'accesso alle proprietà di SharePoint, vedere [classe SPFeaturePropertyCollection](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 I valori delle proprietà funzionalità identici per tutti gli elementi di progetto vengono uniti nel manifesto della funzionalità. Tuttavia, se due diversi elementi del progetto specificano la stessa chiave di proprietà di funzione con valori non corrispondenti, si verifica un errore di convalida.  
  
 Per aggiungere le proprietà della funzionalità direttamente al file di funzionalità (*. feature), chiamare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metodo modello a oggetti SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Se si utilizza questo metodo, tenere presente che la stessa regola sull'aggiunta di valori di proprietà di funzionalità identiche nelle proprietà della funzionalità si applica anche alle proprietà aggiunta direttamente al file di funzionalità.  
  
## <a name="feature-receiver"></a>Ricevitore di funzionalità  
 Ricevitori di funzionalità sono codice eseguito quando si verificano determinati eventi di un elemento di progetto che contiene funzionalità. Ad esempio, è possibile definire i ricevitori di funzionalità che vengono eseguite quando la funzionalità è installata, attivata o aggiornata. Un modo per aggiungere un ricevitore di funzionalità consiste nell'aggiungerlo direttamente a una funzionalità, come descritto [procedura dettagliata: aggiungere ricevitori di eventi](../sharepoint/walkthrough-add-feature-event-receivers.md). È inoltre possibile fare riferimento a un nome di classe ricevitore di funzionalità e un assembly nel **ricevitore di funzionalità** proprietà.  
  
### <a name="direct-method"></a>Metodo diretto  
 Quando si aggiunge un ricevitore di funzionalità a una funzionalità direttamente, un file di codice viene inserito il **funzionalità** nodo in Esplora soluzioni. Quando si compila la soluzione di SharePoint, il codice viene compilato in un assembly e della distribuzione in SharePoint. Per impostazione predefinita, le proprietà della funzionalità **Assembly del ricevitore** e **classe del ricevitore** fa riferimento il nome della classe e l'assembly.  
  
### <a name="reference-method"></a>Reference (metodo)  
 È possibile aggiungere un ricevitore di funzionalità mediante il **ricevitore di funzionalità** proprietà di un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità. Il valore della proprietà ricevitore di funzionalità presenta due sottoproprietà: **Assembly** e **nome classe**. L'assembly è necessario utilizzare il nome completo, nome "sicuro" e il nome della classe deve essere il nome completo del tipo. Per altre informazioni, vedere [Assembly con nomi sicuri](http://go.microsoft.com/fwlink/?LinkID=169573). Dopo aver distribuito la soluzione in SharePoint, la funzione utilizza il ricevitore di funzionalità di cui viene fatto riferimento per gestire gli eventi di funzionalità.  
  
 In fase di compilazione di soluzioni, i valori di proprietà di ricevitore di funzionalità nella funzionalità e i relativi progetti unire tra loro per impostare gli attributi vengono e ReceiverClass dell'elemento Feature nel manifesto della funzionalità del file di soluzione (con estensione wsp) di SharePoint. Pertanto, se vengono specificati entrambi i valori delle proprietà Assembly e il nome di classe di un elemento di progetto e una funzionalità, i valori di proprietà funzionalità e di elemento di progetto devono corrispondere. Se i valori non corrispondono, si riceverà un errore di convalida. Se si desidera che un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità diverso da quello utilizzato dalla relativa funzionalità, spostarlo in un'altra funzionalità.  
  
 Se si fa riferimento a un assembly del ricevitore di funzionalità che non sia già nel server, è necessario includere anche il file di assembly nel pacchetto. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non aggiunge automaticamente. Quando si distribuisce la funzionalità, il file di assembly viene copiato del sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o nella cartella Bin nella directory fisica di SharePoint. Per ulteriori informazioni, vedere Procedura: [procedura: aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per ulteriori informazioni sui ricevitori di funzionalità, vedere [ricevitore di eventi](http://go.microsoft.com/fwlink/?LinkID=169574) e [eventi di funzionalità](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Riferimenti all'output del progetto  
 La proprietà di riferimenti all'Output del progetto specifica una dipendenza, ad esempio un assembly, che deve eseguire l'elemento di progetto. Si supponga, ad esempio, che la soluzione contiene un progetto di integrazione applicativa dei dati e un progetto di classe. Se il progetto di integrazione applicativa dei dati ha una dipendenza dall'assembly che è l'output dal progetto di classe, è possibile fare riferimento l'assembly nella proprietà di riferimenti all'Output del progetto di integrazione applicativa dei dati del progetto. Quando il progetto viene compresso, l'assembly dipendente viene incluso nel pacchetto.  
  
 Riferimenti all'output del progetto sono in genere gli assembly, ma in alcuni casi (ad esempio progetti Silverlight) possono essere altri tipi di file.  
  
 Per ulteriori informazioni, vedere [procedura: aggiungere un riferimento all'Output del progetto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Voci di controllo sicure  
 SharePoint fornisce un meccanismo di sicurezza, denominato voci di controllo sicure, per limitare l'accesso degli utenti non attendibili di determinati controlli. Per impostazione predefinita, SharePoint consente agli utenti non attendibili di caricare e creare pagine ASPX nel server SharePoint. Per impedire agli utenti di aggiungere codice unsafe alle pagine ASPX, SharePoint consente di limitare l'accesso al *controlli sicuri*. Controlli sicuri sono controlli ASPX e Web part designata come protetto e che può essere utilizzato da qualsiasi utente del sito. Per ulteriori informazioni, vedere [passaggio 4: aggiungere la Web Part per l'elenco di controlli sicuri](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Ogni elemento di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ha una proprietà denominata **voci di controllo sicure** che presenta due sottoproprietà booleane: **provvisoria** e **sicurezza Script**. Con la proprietà Sicuro viene specificato se gli utenti non attendibili possono accedere a un controllo. La proprietà di sicurezza Script specifica se gli utenti non attendibili possono visualizzare e modificare le proprietà di un controllo.  
  
 Voci di controllo sicure vengono fatto riferimento in base all'assembly. Per aggiungere voci di controllo sicure all'assembly di un progetto immesse nell'elemento di progetto **voci di controllo sicure** proprietà. Tuttavia, è possibile aggiungere voci di controllo sicure per l'assembly di un progetto tramite la **avanzate** nella scheda il **Progettazione pacchetti** quando si aggiunge un assembly aggiuntivo al pacchetto. Per ulteriori informazioni, vedere [come: contrassegna i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [registrazione di un Assembly di Web Part come SafeControl](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Voci di XML per i controlli sicuri  
 Quando si aggiunge una voce di controllo sicura a un elemento di progetto o assembly del progetto, viene scritto un riferimento al manifesto di pacchetto nel formato seguente:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Assemblaggio e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilizzo di moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  