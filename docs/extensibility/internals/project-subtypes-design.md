---
title: Sottotipi di progetto progettazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>Sottotipi di progetto
Sottotipi di progetto consentono VSPackage estendono progetti basati su Microsoft Build Engine (MSBuild). L'utilizzo di aggregazioni consente di riutilizzare la maggior parte del sistema del progetto principale gestite implementata in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ancora comunque personalizzare il comportamento per un determinato scenario.  
  
 Gli argomenti seguenti descrivono la struttura di base e l'implementazione dei sottotipi di progetto:  
  
-   Sottotipo di progetto.  
  
-   Aggregazione di più livelli.  
  
-   Supporto di interfacce.  
  
## <a name="project-subtype-design"></a>Sottotipo di progetto  
 L'inizializzazione di un sottotipo di progetto viene ottenuta mediante l'aggregazione principale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> oggetti. Questa aggregazione consente un sottotipo di progetto eseguire l'override o migliorare la maggior parte delle funzionalità del progetto di base. Sottotipi di progetto ottenere la prima opportunità di gestire le proprietà utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, utilizzando i comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e gestione di elementi di progetto mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Sottotipi di progetto è anche possono estendere:  
  
-   Oggetti di configurazione di progetto.  
  
-   Oggetti dipendenti dalla configurazione.  
  
-   Oggetti Sfoglia indipendenti dalla configurazione.  
  
-   Oggetti di automazione di progetto.  
  
-   Raccolte di proprietà di automazione del progetto.  
  
 Per ulteriori informazioni sull'estensibilità per sottotipi di progetto, vedere [proprietà e metodi estesi per i sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>File dei criteri  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente fornisce un esempio di estensione del sistema di progetto di base con un sottotipo di progetto nella sua implementazione di file dei criteri. Un file di criteri consente il data shaping del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente mediante la gestione delle funzionalità di Esplora soluzioni, **Aggiungi progetto** nella finestra di dialogo **Aggiungi nuovo elemento** la finestra di dialogo e  **Proprietà** la finestra di dialogo. Il sottotipo di criteri esegue l'override e migliora tali funzionalità tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementazioni.  
  
##### <a name="aggregation-mechanism"></a>Meccanismo di aggregazione  
 Meccanismo di aggregazione sottotipo di progetto dell'ambiente supporta più livelli di aggregazione, consentendo in tal modo un sottotipo avanzato implementate da altre flavoring del progetto. Inoltre, gli oggetti di supporto di un progetto di sottotipo, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sono progettati per consentire a più livelli di sovrapposizione. In conformità con i vincoli di COM e COM le regole di aggregazione, sottotipi di progetto e progetti di base devono essere programmate in modo cooperativo per consentire il sottotipo interno o il progetto di base di partecipare correttamente a delegare le chiamate di metodo e la gestione di conteggi dei riferimenti . Il progetto sta per essere aggregati, ovvero deve essere programmato per supportare l'aggregazione.  
  
 Nella figura seguente mostra una rappresentazione schematica di un'aggregazione sottotipo di progetto a più livelli.  
  
 ![Rappresentazione grafica di Visual Studio projectflavor a più livelli](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Sottotipo di progetto più livelli  
  
 Un'aggregazione sottotipo di progetto a più livelli è costituito da tre livelli, un progetto di base, che viene aggregato da un sottotipo di progetto, quindi ulteriormente aggregati da un sottotipo avanzate del progetto. Nella figura illustra alcune delle interfacce che vengono fornite come parte del supporto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architettura sottotipo del progetto.  
  
##### <a name="deployment-mechanisms"></a>Meccanismi di distribuzione  
 Tra tanti di base del sistema di progetto migliorate mediante un sottotipo di progetto le funzionalità sono meccanismi di distribuzione. Un sottotipo del progetto influisce sui meccanismi di distribuzione mediante l'implementazione di interfacce di configurazione (ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) che vengono recuperati tramite una chiamata QueryInterface sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. In uno scenario in cui sia il sottotipo di progetto e il sottotipo avanzate del progetto aggiungere implementazioni diverse di configurazione, il progetto di base chiama `QueryInterface` il sottotipo di progetto avanzate `IUnknown`. Se il sottotipo di progetto interna contiene l'implementazione di configurazione che richiede un tipo di progetto di base, il sottotipo di progetto avanzate delega per l'implementazione fornita per il sottotipo di progetto interna. Come un meccanismo per rendere persistente lo stato dal livello di uno aggregazione a altro, tutti i livelli dei sottotipi di progetto implementano <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> in modo permanente non compilazione correlati dati XML nei file di progetto. Per ulteriori informazioni, vedere [persistenza dei dati nel File di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>viene implementato come un meccanismo per recuperare i sottotipi di progetto di Extender di automazione.  
  
 Nella figura seguente è incentrata sull'implementazione di extender di automazione, l'oggetto di esplorazione di configurazione di progetto, in particolare, utilizzato da sottotipi di progetto per estendere il sistema di progetto di base.  
  
 ![Rappresentazione grafica di Extender automatico delle caratteristiche progetto VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Estensione di automazione sottotipo di progetto.  
  
 Sottotipi di progetto è possono estendere ulteriormente il sistema del progetto di base estendendo il modello oggetto di automazione. Questi sono definiti come parte dell'oggetto di automazione DTE e vengono utilizzati per estendere l'oggetto di progetto, il `ProjectItem` oggetto e `Configuration` oggetto. Per ulteriori informazioni, vedere [estendendo il modello a oggetti del progetto di Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Aggregazione di più livelli  
 Un'implementazione di sottotipo di progetto che include un sottotipo di progetto di livello inferiore deve essere programmate in modo cooperativo per consentire il sottotipo di progetto interna funzionare correttamente. Include un elenco di competenze di programmazione:  
  
-   Il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementazione del sottotipo di progetto che esegue il wrapping il sottotipo interno deve delegare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementazione del sottotipo di progetto interna per entrambi <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metodi.  
  
-   Il <xref:EnvDTE80.IInternalExtenderProvider> implementazione del sottotipo di progetto di wrapper deve delegare a quella dei relativi sottotipi di progetto interna. In particolare, l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> deve recuperare la stringa di nomi dal sottotipo di progetto interna e quindi concatenare le stringhe in cui desidera aggiungere come Extender.  
  
-   Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> deve creare un'istanza dell'implementazione di un sottotipo di progetto wrapper di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> oggetto del relativo interna sottotipo di progetto e tenerla premuta, come un delegato privato, poiché solo l'oggetto di configurazione di progetto di base del progetto direttamente riconosce che il wrapper oggetto di configurazione sottotipo di progetto esistente. Il sottotipo di progetto esterno può scegliere inizialmente le interfacce di configurazione che si desidera gestire in modo diretto e quindi delegare il resto all'implementazione del sottotipo di progetto interna di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Supporto di interfacce  
 Il progetto di base delega le chiamate al supporto di interfacce aggiunte da un sottotipo di progetto, per estendere i vari aspetti della relativa implementazione. Ciò include l'estensione gli oggetti di configurazione di progetto e di vari oggetti di proprietà browser. Queste interfacce vengono recuperate chiamando `QueryInterface` su `punkOuter` (un puntatore al `IUnknown`) di Sil aggregator sottotipo di progetto più esterno.  
  
|Interfaccia|Sottotipo di progetto|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente il sottotipo di progetto per:<br /><br /> -Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Controllo dell'avvio del debugger, consentendo il sottotipo di progetto fornire la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Disabilita la valutazione dell'espressione in fase di progettazione gestendo in modo appropriato il `DBGLAUNCH_DesignTimeExprEval` case nella sua implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente il sottotipo di progetto per:<br /><br /> -Consente di estendere il <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> del progetto per aggiungere o rimuovere proprietà indipendente di configurazione del progetto.<br />-Consente di estendere l'oggetto di automazione di progetto (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) del progetto.<br /><br /> I valori delle proprietà sopra vengono prelevati <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> enumerazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente il sottotipo di progetto eseguire nuovamente il mapping di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto dato l'oggetto di esplorazione di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente il sottotipo di progetto eseguire nuovamente il mapping di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> o `VSITEMID` oggetto, dato l'oggetto di esplorazione di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente il sottotipo di progetto rendere persistenti i dati XML strutturati arbitrari al file di progetto (con estensione vbproj o csproj). Questi dati non sono visibili a MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente il sottotipo di progetto per:<br /><br /> -Aggiungere nuove proprietà di MSBuild che deve essere mantenuta.<br />-Rimuovere proprietà necessaria da MSBuild.<br />-Query per il valore corrente di una proprietà di MSBuild.<br />-Modificare il valore corrente di una proprietà di MSBuild.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>