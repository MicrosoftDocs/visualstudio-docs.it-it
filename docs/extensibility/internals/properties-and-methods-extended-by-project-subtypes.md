---
title: Proprietà e metodi estesi per i sottotipi di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi per i sottotipi di progetto
Un sottotipo di progetto è un potente per influenzare il comportamento del progetto perché viene costruito un aggregatore di un progetto di base. Questa sezione riepiloga alcune delle funzionalità che può essere migliorata o modificata da sottotipi di progetto.  
  
## <a name="features-gained-by-aggregation"></a>Funzionalità acquisita da un'aggregazione  
 Nella tabella seguente sono riepilogate molti dei metodi che consente l'aggregazione sottotipi di progetto eseguire l'override nei progetti di base.  
  
|Metodi di override da parte di aggregazione|Sottotipo di progetto|  
|---------------------------------------|---------------------|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Consente a un sottotipo del progetto<br /><br /> -Modificare didascalia e l'icona del nodo di progetto.<br />-Eseguire l'override completamente progetto `Browse` oggetto.<br />-Controllare se è possibile rinominare progetto.<br />-Controllo di ordinamento.<br />-Contesto utente controllo per la Guida dinamica.|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto controllare quali servizi contestuali vengono forniti agli editor e finestre di progettazione.|  
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Consente a un sottotipo del progetto<br /><br /> -Partecipare del routing dei comandi per i comandi di progetto.<br />-Aggiungere, rimuovere o disabilitare i comandi di ambiente di progetto e comandi attivi di Esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Consente il sottotipo di progetto filtrare quanto visualizzato nel **Aggiungi nuovo elemento** la finestra di dialogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Consente a un sottotipo del progetto<br /><br /> -Determinare il generatore predefinito assegnato a un'estensione di file.<br />-Mapping di un nome generatore leggibile umano a un oggetto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Proprietà utilizzati dalle sottotipi di progetto  
 Il sistema del progetto di base e l'ambiente è possibile utilizzare le proprietà da <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> enumerazioni descritti nella tabella seguente per abilitare un sottotipo di progetto controllare varie funzionalità del sistema del progetto.  
  
|Proprietà VSHPROPID|Sottotipo di progetto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Consente a un sottotipo di progetto controllare il contenuto del **Aggiungi elemento** la finestra di dialogo. Il sottotipo di progetto può fornire una nuova specifica di directory di modello, aggiungere nuovi tipi di elementi, rimuovere gli elementi esistenti e la riorganizzazione di un subset di elementi del progetto di base **Aggiungi elemento** la finestra di dialogo.|  
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere pagine delle proprietà indipendenti dalla configurazione.|  
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere pagine delle proprietà dipendenti dalla configurazione.|  
|`ExtObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per il progetto o il progetto oggetti elemento conoscendo il CATID Extender. Ad esempio, un sottotipo di progetto può fornire un oggetto personalizzato `Project.Extender("<subtype>")` oggetto.|  
|`BrowseObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per il `Browse` oggetto conoscendo il CATID Extender. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive per il <xref:EnvDTE.Project.Properties%2A> insieme.|  
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per l'oggetto di esplorazione di configurazione di progetto. Ad esempio, un sottotipo di progetto può aggiungere proprietà aggiuntive per il <xref:EnvDTE.Configuration.Properties%2A> insieme.|  
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto fornire un Extender di automazione per l'oggetto di configurazione.|  
|`DefaultPlatformName`|Consente a un sottotipo di progetto determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|  
  
 Il progetto di base fornisce un'implementazione predefinita di queste proprietà. Il progetto di base ottiene queste informazioni chiamando `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> il sottotipo di progetto più esterno, consentendo in tal modo il sottotipo di progetto per l'override dell'implementazione delle proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)