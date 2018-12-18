---
title: Che contribuiscono al modello di automazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb69380913f188031c97b46530ea2659fc05fe30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-automation-model"></a>Che contribuiscono al modello di automazione
Visual Studio fornisce un set di interfacce di automazione per personalizzare l'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti di creare componenti aggiuntivi di Visual Studio ed estensioni.  
  
 Inoltre, è opportuno, lo sviluppatore di un VSPackage per contribuire al modello di automazione; In questo modo, è consentire agli utenti finali di un VSPackage per creare componenti aggiuntivi e in genere offrire un'esperienza di modello uniforme durante l'utilizzo VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per rendere l'utente finale esperienza coerente, è possibile seguire una serie di linee guida quando si progetta il pacchetto VSPackage in modo che il modello di automazione per il pacchetto VSPackage segue le idee in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)  
 Definisce il modello di automazione come correlati a un gruppo di oggetti che controllano i principali aspetti dell'ambiente comune. Questo set di oggetti è raffigurato in un diagramma del modello di automazione.  
  
 [Automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Vengono illustrati i due modi per fornire l'automazione per il pacchetto VSPackage.  
  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)  
 Vengono fornite istruzioni dettagliate per la creazione di oggetti specifici del VSPackage.  
  
 [Definizione di modelli di progetto](../../extensibility/internals/project-modeling.md)  
 Vengono illustrati gli oggetti di progetto standard che sono necessarie per creare l'automazione per il nuovo tipo di progetto e viene illustrato il percorso che segue automazione del progetto. In questo argomento vengono anche forniti elenchi di dichiarazioni e implementazioni per le classi.  
  
 [Esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.  
  
 [Supporto dell'automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)  
 Viene descritto come restituire un oggetto di automazione per il supporto delle proprietà di un VSPackage personalizzato **opzioni** della finestra di dialogo di **strumento** menu estendendo il `DTE.Properties` oggetto.  
  
 [Automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)  
 Viene illustrato che la creazione di un modello di automazione per il codice non è necessaria. Tuttavia, in questo argomento vengono fornite informazioni utili nei modelli di codice viene fornito un collegamento.  
  
 [Procedura: Fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Viene spiegato che fornisce l'automazione è una buona idea ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronti all'uso. Viene illustrata l'automazione per le finestre degli strumenti e finestre di documento.  
  
 [Uso del modello di automazione](../../extensibility/internals/using-the-automation-model.md)  
 Fornisce due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto iniziale gli oggetti di automazione.  
  
 [Automazione per la configurazione e per gli oggetti SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Vengono fornite informazioni sull'automazione per le opzioni di configurazione e l'automazione per gli elementi selezionati.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornisce un esempio di codice che illustra come fa parte di un pacchetto VSPackage nel modello a oggetti di automazione DTE. Vengono elencati parametri, valori restituiti e osservazioni selezionati.  
  
## <a name="related-sections"></a>Sezioni correlate