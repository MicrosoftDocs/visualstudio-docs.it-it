---
title: Fornisce l'automazione per pacchetti VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="providing-automation-for-vspackages"></a>Fornisce l'automazione per pacchetti VSPackage
Esistono due modi per fornire l'automazione per VSPackage: mediante l'implementazione degli oggetti specifici di VSPackage e implementando gli oggetti di automazione standard. In genere, questi vengono utilizzati insieme per estendere il modello di automazione dell'ambiente.  
  
## <a name="vspackage-specific-objects"></a>Oggetti specifici di VSPackage  
 Determinate posizioni all'interno del modello di automazione richiedono di fornire oggetti di automazione sono univoci per il pacchetto VSPackage. Ad esempio, i nuovi progetti richiedono oggetti distinti che fornisce solo il pacchetto VSPackage. I nomi di questi oggetti vengono immessi nel Registro di sistema e ottenuti tramite chiamate all'ambiente `DTE` oggetto.  
  
 È possibile ottenere oggetti specifici del pacchetto VSPackage anche quando un consumer di automazione utilizza l'oggetto fornito tramite la proprietà dell'oggetto di un oggetto standard. Ad esempio, lo standard `Window` oggetto ha un `Object` proprietà, comunemente noti come il `Windows.Object` proprietà. Quando i consumer chiamano il `Window.Object` in una finestra implementata nel pacchetto VSPackage, passare nuovamente un oggetto di automazione specifico della finestra di progettazione.  
  
#### <a name="projects"></a>Progetti  
 Pacchetti VSPackage possono estendere il modello di automazione per i nuovi tipi di progetto tramite i propri oggetti VSPackage specifici. Lo scopo principale di fornire i nuovi oggetti di automazione per il pacchetto VSPackage è possibile distinguere il progetto univoco gli oggetti da un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o <xref:VSLangProj80.VSProject2> oggetto. Questa distinzione è utile quando si desidera fornire un modo per singolo o eseguire l'iterazione di un tipo di progetto a parte di altri tipi di progetto deve side-by-side vengono visualizzati in una soluzione. Per ulteriori informazioni, vedere [esposizione di oggetti del progetto](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Eventi  
 L'architettura di evento dell'ambiente offre un'altra posizione, è possibile aggiungere oggetti personalizzati specifici di VSPackage. Tramite la creazione di oggetti evento univoco, ad esempio, è possibile estendere il modello di eventi dell'ambiente per i progetti. Si può ritenere opportuno fornire i propri eventi quando un nuovo elemento viene aggiunto al tipo di progetto. Per ulteriori informazioni, vedere [esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Oggetti finestra  
 Windows può passare nuovamente un oggetto di automazione specifico VSPackage all'ambiente quando viene chiamato. Implementare un oggetto derivato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> o `IDispatch` che passa indietro di proprietà, si estende la classe di finestra in cui viene individuato. Ad esempio, è possibile utilizzare questo approccio per fornire l'automazione per un controllo inserito in una cornice di finestra. La semantica di questo oggetto e tutti gli altri oggetti che è possibile estendere è quelle in uso per la progettazione. Per ulteriori informazioni, vedere [procedura: fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pagine Opzioni del menu Strumenti  
 È possibile creare pagine per estendere gli strumenti, il modello di automazione opzioni tramite l'implementazione delle pagine e aggiungere informazioni al Registro di sistema per creare le proprie opzioni. Le pagine quindi possono essere chiamate tramite il modello a oggetti ambiente come tutte le altre pagine di opzioni. Se la progettazione della funzionalità per aggiungere l'ambiente tramite VSPackage richiede che le pagine di opzioni, è necessario aggiungere anche il supporto di automazione. Per ulteriori informazioni, vedere [il supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Oggetti di automazione standard  
 Per estendere l'automazione per i progetti, si implementano anche gli oggetti di automazione standard (derivato da `IDispatch`) che stand accanto ad altri oggetti di progetto e implementare i metodi e proprietà standard. Esempi di oggetti standard sono gli oggetti di progetto che vengono inseriti nella gerarchia della soluzione, ad esempio `Projects`, `Project`, `ProjectItem`, e `ProjectItems`. Ogni nuovo tipo di progetto deve implementare questi oggetti (e possibilmente altri in base alla semantica del progetto).  
  
 In un certo senso, questi oggetti offrono il vantaggio degli oggetti di progetto VSPackage specifiche opposto. Gli oggetti di automazione standard consentono il progetto da utilizzare in modo generalizzato come qualsiasi altro progetto gli stessi oggetti di supporto. Di conseguenza, un componente aggiuntivo che viene scritto su Generale `Project` e `ProjectItem` gli oggetti in grado di funzionare per i progetti di qualsiasi tipo. Per ulteriori informazioni, vedere [progetto di modellazione](../../extensibility/internals/project-modeling.md).