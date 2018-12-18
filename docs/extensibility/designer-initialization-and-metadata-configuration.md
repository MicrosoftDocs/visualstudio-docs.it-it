---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61624d9926f4d984386f1a8b3fe8a575ce465331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati
Modifica degli attributi dei metadati e di filtro associata a una finestra di progettazione o di un componente di progettazione fornisce un meccanismo definire gli strumenti vengono utilizzati da una particolare finestra di progettazione per gestire diverse applicazioni <xref:System.Type> oggetti (ad esempio le strutture di dati, le classi, o entità con interfaccia grafica), quando non è disponibile la finestra di progettazione e configurazione per supportare la finestra di progettazione IDE di Visual Studio (per istanza cui **della casella degli strumenti** categoria o la scheda è disponibile).  
  
 Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] offre diversi meccanismi per facilitare il controllo dell'inizializzazione di un componente di progettazione della finestra di progettazione e la manipolazione dei metadati da un pacchetto VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inizializzazione di metadati e le informazioni di configurazione  
 Poiché vengono caricati su richiesta, VSPackage potrebbero non sono stati caricati dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente prima della creazione di istanze di una finestra di progettazione. Pertanto, VSPackage non è possibile utilizzare il meccanismo standard per la configurazione di una finestra di progettazione o di un componente della finestra di progettazione al momento della creazione, ovvero per gestire un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento. Al contrario, un pacchetto VSPackage implementa un'istanza del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> l'interfaccia e si registra per fornire le personalizzazioni, detti estensioni della superficie di progettazione.  
  
### <a name="customizing-initialization"></a>Personalizzazione di inizializzazione  
 Personalizzazione di una finestra di progettazione, un componente o un'area di progettazione include:  
  
1.  Modifica i metadati della finestra di progettazione e la modifica in modo efficace la modalità di un determinato <xref:System.Type> accedere o convertiti.  
  
     Questa operazione viene in genere eseguita tramite il <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.TypeConverter> meccanismi.  
  
     Ad esempio, quando <xref:System.Windows.Forms>-basata su finestre di progettazione vengono inizializzati, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente modifica il <xref:System.Drawing.Design.UITypeEditor> per <xref:System.Web.UI.WebControls.Image> gli oggetti usati con la finestra di progettazione per utilizzare il gestore delle risorse per ottenere le bitmap anziché nel file system.  
  
2.  L'integrazione con l'ambiente, ad esempio, per la sottoscrizione di eventi o per ottenere informazioni sulla configurazione di progetto. È possibile ottenere informazioni sulla configurazione di progetto e sottoscrivere eventi ottenendo il <xref:System.ComponentModel.Design.ITypeResolutionService> interfaccia.  
  
3.  Modifica dell'ambiente utente attivando appropriato **della casella degli strumenti** categorie o limitando l'applicabilità della finestra di progettazione tramite l'applicazione di un'istanza del <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe nella finestra di progettazione.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da un pacchetto VSPackage  
 Un pacchetto VSPackage deve gestire l'inizializzazione della finestra di progettazione mediante:  
  
1.  Creazione di un oggetto che implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.  
  
    > [!NOTE]
    >  Il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe mai deve essere implementata per l'oggetto stesso come il <xref:Microsoft.VisualStudio.Shell.Package> classe.  
  
2.  Registrare la classe che implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> come fornire supporto per le estensioni della finestra di progettazione del pacchetto VSPackage applicando le istanze di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> per la classe che fornisce l'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Ogni volta che viene creata una qualsiasi finestra di progettazione o di un componente di progettazione, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
1.  Accede a ogni provider di estensione della superficie di progettazione registrati.  
  
2.  Crea e inizializza un'istanza di ciascun provider di estensione della superficie di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetto  
  
3.  Chiama ogni provider di estensione della superficie di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> metodo o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (metodo) (se necessario).  
  
 Quando si implementa il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> dell'oggetto come un membro di un VSPackage, è importante comprendere che:  
  
1.  Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente consentono di controllare tutti i metadati o altre impostazioni di configurazione una particolare `DesignSurfaceExtension` modifica del provider. È possibile che due o più `DesignSurfaceExtension` provider modifica la stessa funzionalità della finestra di progettazione in modalità in conflitto, con l'ultima modifica da definitivo. È indeterminato quale modifica viene applicata.  
  
2.  È possibile limitare in modo esplicito un'implementazione del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> specifiche finestre di progettazione, applicando le istanze di oggetto <xref:System.ComponentModel.ToolboxItemFilterAttribute> al tipo di implementazione. Per ulteriori informazioni su **della casella degli strumenti** elemento filtro, vedere il <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Provisioning di metadati aggiuntivi  
 Un pacchetto VSPackage può modificare la configurazione di una finestra di progettazione o di un componente della finestra di progettazione diverso in fase di progettazione.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere utilizzata a livello di codice o essere applicato a un VSPackage che fornisce una finestra di progettazione.  
  
 Un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe viene utilizzata per modificare i metadati dei componenti creati su un'area di progettazione. Ad esempio, una possibile sostituire un visualizzatore di proprietà predefinito utilizzato da <xref:System.Windows.Forms.CommonDialog> oggetti, con un browser di proprietà personalizzata.  
  
 Modifiche fornite da un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> applicato a un'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Package> può avere uno dei due ambiti:  
  
-   Global - per tutte le nuove istanze di un determinato componente  
  
-   Locale - si riferisce solo all'istanza del componente creato nell'area di progettazione fornita dal pacchetto VSPackage corrente.  
  
 Il `IsGlobal` proprietà del <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> applicato a un'implementazione di VSPackage istanza <xref:Microsoft.VisualStudio.Shell.Package> determina l'ambito.  
  
 Applicando l'attributo a un'implementazione di <xref:Microsoft.VisualStudio.Shell.Package> con il <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> proprietà del <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> oggetto impostato su `true`, come indicato di seguito, viene modificato il browser per l'intero [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Se il flag globale è stato impostato su `false`, la modifica dei metadati è locale per la finestra di progettazione corrente è supportata dal pacchetto VSPackage corrente:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  Al momento, l'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere i metadati locali. Nell'esempio precedente, si stava tentando di modificare una proprietà, ad esempio il `Color` proprietà di un oggetto. Se `false` passato per il flag globale, `CustomBrowser` non verranno visualizzati perché la finestra di progettazione crea mai un'istanza di `Color`. Impostazione del flag globale `false` è utile per i componenti, ad esempio i controlli, timer e le finestre di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Estensione del supporto in fase di progettazione](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)