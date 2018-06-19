---
title: Interfaccia utente delle proprietà del progetto | Documenti Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 788107666f8103a77753b93fa7c1febc73f9b97f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132427"
---
# <a name="project-property-user-interface"></a>Interfaccia utente di proprietà del progetto
Un sottotipo di progetto è possibile usare gli elementi del progetto **pagine delle proprietà** la finestra di dialogo come vengono forniti dal progetto di base, nascondere o rendere intere pagine e controlli di sola lettura come fornito o aggiungere pagine specifici del sottotipo di progetto per il **Pagine delle proprietà** la finestra di dialogo.

## <a name="extending-the-project-property-dialog-box"></a>La finestra di dialogo delle proprietà del progetto di estensione
 Un sottotipo di progetto implementa Extender di automazione e visualizzare oggetti di configurazione progetto. Implementano queste estensioni di <xref:EnvDTE.IFilterProperties> interfaccia particolari proprietà nascosti o di sola lettura. Il **pagine delle proprietà** la finestra di dialogo del progetto di base, implementato dal progetto di base, viene eseguita da estensioni di automazione il filtro.

 Il processo di espansione un **proprietà del progetto** la finestra di dialogo viene indicata di seguito:

-   Il progetto di base recupera le estensioni dal sottotipo del progetto mediante l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> interfaccia. Lo Sfoglia, automazione dei progetti e gli oggetti Sfoglia di configurazione di progetto del progetto di base tutti implementano questa interfaccia.

-   L'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> per delegare l'oggetto di esplorazione di progetto e l'oggetto di automazione di progetto di <xref:EnvDTE80.IInternalExtenderProvider> implementazione di Sil aggregator sottotipo di progetto (vale a dire che `QueryInterface` per <xref:EnvDTE80.IInternalExtenderProvider> sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto di progetto).

-   Implementa inoltre l'oggetto di progetto di base configurazione Sfoglia <xref:EnvDTE80.IInternalExtenderProvider> associare direttamente l'estensione di automazione dall'oggetto di configurazione del sottotipo di progetto. L'implementazione di delega per il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata da Sil aggregator sottotipo di progetto.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementato dall'oggetto progetto Sfoglia configuration, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, inoltre implementate dall'oggetto Sfoglia configurazione progetto, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto.

-   Un sottotipo di progetto è possibile determinare il CATID appropriato per gli oggetti estensibili varie del progetto di base in fase di esecuzione tramite il recupero dei seguenti <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valori:

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

Per determinare il CATID per l'ambito di progetto, il sottotipo del progetto recupera proprietà sopra menzionate per [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) dal `VSITEMID typedef`. Un sottotipo di progetto potrebbe essere anche di controllare quali **pagine delle proprietà** schede dialogo vengono visualizzati per il progetto, le configurazioni dipendenti e indipendenti di configurazione. Alcuni sottotipi di progetto potrebbero essere necessario rimuovere le pagine predefinite e aggiungere pagine specifiche sottotipo di progetto. Per abilitare questa opzione, il progetto di client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo per le proprietà seguenti:

-   `VSHPROPID_PropertyPagesCLSIDList` ovvero un elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` un elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.

Poiché il progetto sottotipo aggregazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dell'oggetto, è possibile eseguire l'override di definizione di queste proprietà per controllare quali **pagine delle proprietà** vengono visualizzate le finestre di dialogo. Il sottotipo del progetto possa recuperare queste proprietà del progetto di base interna e quindi aggiungere o rimuovere CLSID in base alle esigenze.

Nuove pagine delle proprietà aggiunte da un sottotipo di progetto vengono assegnate a un oggetto configurazione progetto rispetto all'implementazione di base di progetto. Questo oggetto configurazione progetto supporta Extender di automazione. Per ulteriori informazioni su AutomationExtenders, vedere [all'implementazione e utilizzo delle estensioni di automazione](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Le pagine delle proprietà implementati mediante la chiamata di sottotipo di progetto <xref:EnvDTE.Project.Extender%2A> per recuperare i propri oggetto project sottotipo configurazione Sfoglia che estende l'oggetto di esplorazione di configurazione del progetto di base.

## <a name="see-also"></a>Vedere anche

- <xref:EnvDTE.IFilterProperties>
- [Finestra di dialogo Pagine delle proprietà](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)