---
title: Unione di codice XML in funzionalità e pacchetto manifesti | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ae4eef0cc0e596f6ecd0848363f51c55b606d4a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Unione di codice XML in manifesti di funzionalità e pacchetto
  Funzionalità e pacchetti sono definiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Questi manifesti di pacchetto sono una combinazione di dati generati da finestre di progettazione e personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] immesso nel modello di manifesto da parte degli utenti. In fase di creazione di pacchetti, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni con progettazione fornita dal [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per formare il package [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Elementi simili, con le eccezioni descritte più avanti in eccezioni di tipo Merge, vengono uniti per evitare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] gli errori di convalida dopo aver distribuito i file in SharePoint e per rendere il manifesto di file più snelli ed efficienti.  
  
## <a name="modifying-the-manifests"></a>Modifica di manifesti  
 È possibile modificare direttamente i file manifesti del pacchetto, fino a quando non si disabilita le finestre di progettazione di funzionalità o il pacchetto. Tuttavia, è possibile aggiungere manualmente personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi al modello di manifesto tramite le finestre di progettazione di funzionalità e del pacchetto o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Per ulteriori informazioni, vedere [procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Processo di Merge manifesti di funzionalità e pacchetto  
 Quando si combinano gli elementi personalizzati insieme a elements fornito, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizza il seguente processo. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Controlla se ogni elemento ha un valore di chiave univoco. Se un elemento non dispone di valori di chiave univoci, viene aggiunto al file manifesto inserito nel pacchetto. Analogamente, gli elementi che dispongono di più chiavi non possono essere sottoposti a merge. Di conseguenza, essi vengono aggiunti al file manifesto.  
  
 Se un elemento contiene una chiave univoca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] confronta i valori della finestra di progettazione e chiavi personalizzate. Se i valori corrispondono, vengono unite in un singolo valore. Se i valori differiscono, viene eliminato il valore della chiave della finestra di progettazione e viene utilizzato il valore della chiave personalizzato. Le raccolte vengono unite anche. Ad esempio, se la finestra di progettazione generati [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personalizzata e [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] sia contiene una raccolta di assembly, il manifesto nel pacchetto contiene solo una raccolta di assembly.  
  
## <a name="merge-exceptions"></a>Eccezioni di tipo merge  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unisce la maggior parte dei progettazione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi insieme personalizzati simili [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi a condizione che dispongono di un singolo attributo di identificazione univoco. Tuttavia, alcuni elementi non includono l'identificatore univoco richiesto per [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] l'unione. Questi elementi sono note come *eccezioni di tipo merge*. In questi casi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non vengono unite personalizzata [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi insieme alla finestra di progettazione fornita dal [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi, ma li aggiunge al file manifesto nel pacchetto.  
  
 Ecco un elenco di eccezioni di tipo merge per funzionalità e pacchetto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto.  
  
|Designer|Elemento XML|  
|--------------|-----------------|  
|Finestra di progettazione di funzionalità|ActivationDependency|  
|Finestra di progettazione di funzionalità|UpgradeAction|  
|Finestra di progettazione pacchetti|SafeControl|  
|Finestra di progettazione pacchetti|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementi del manifesto di funzionalità  
 Nella tabella seguente è un elenco di tutti gli elementi del manifesto di funzionalità che possono essere uniti e la relativa chiave univoca che viene utilizzato per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|------------------|----------------|  
|Funzionalità (tutti gli attributi)|*Nome dell'attributo* (ogni nome di attributo dell'elemento Feature è una chiave univoca).|  
|ElementFile|Percorso|  
|ElementManifests/ElementManifest|Percorso|  
|Proprietà o la proprietà|Chiave|  
|CustomUpgradeAction|nome|  
|CustomUpgradeActionParameter|nome|  
  
> [!NOTE]  
>  Poiché è l'unico modo per modificare l'elemento CustomUpgradeAction personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, l'effetto di unione non è bassa.  
  
## <a name="package-manifest-elements"></a>Elementi del manifesto di pacchetto  
 Nella tabella seguente è un elenco di tutti gli elementi del manifesto di pacchetto che possono essere uniti e la relativa chiave univoca che viene utilizzato per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|------------------|----------------|  
|Soluzione (tutti gli attributi)|*Nome dell'attributo* (ogni nome di attributo dell'elemento di soluzione è una chiave univoca).|  
|Elemento ApplicationResourceFiles/ApplicationResourceFile|Percorso|  
|Assembly/Assembly|Percorso|  
|ClassResources/ClassResource|Percorso|  
|DwpFiles/dwp|Percorso|  
|FeatureManifests/FeatureManifest|Percorso|  
|Le risorse o risorse|Percorso|  
|RootFiles/RootFile|Percorso|  
|SiteDefinitionManifests/SiteDefinitionManifest|Percorso|  
|WebTempFile|Percorso|  
|Modellofile/TemplateFile|Percorso|  
|SolutionDependency|IDSoluzione|  
  
## <a name="manually-add-deployed-files"></a>Aggiungere manualmente i file distribuiti  
 Alcuni elementi del manifesto, ad esempio ApplicationResourceFile e DwpFiles, specificano un percorso che include un nome di file. Tuttavia, aggiunta di una voce di nome file per il modello di manifesto non aggiungere il file sottostante al pacchetto. È necessario aggiungere il file al progetto per includerlo nel pacchetto e impostarne la proprietà di tipo di distribuzione, di conseguenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del package e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  