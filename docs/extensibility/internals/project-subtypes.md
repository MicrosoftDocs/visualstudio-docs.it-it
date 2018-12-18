---
title: Sottotipi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 21d7f013989607f7f5416a57829bc9b2b29b61d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes"></a>Sottotipi di progetto
Sottotipi di progetto consentono di personalizzare o flavor il comportamento dei sistemi di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Le personalizzazioni includono il salvataggio di dati aggiuntivi nel file di progetto, aggiungendo o filtrando gli elementi il **Aggiungi nuovo elemento** nella finestra di dialogo controllo modalità di debug e di distribuito, assembly e il progetto di estensione **proprietà Pagine** la finestra di dialogo. I pacchetti VSPackage implementare sottotipi di progetto utilizzando l'aggregazione COM.  
  
> [!NOTE]
>  Il sistema di progetto Visual C++ non supporta sottotipi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]stesso Usa sottotipi di progetto per implementare progetti SQL Server e Smart Device.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)  
 Viene descritto il concetto di sottotipi di progetto.  
  
 [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Viene descritta la sequenza di inizializzazione sottotipo di progetto a livello di codice da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Vengono fornite descrizioni dettagliate delle funzionalità e dei metodi più di frequente estesi usando sottotipi di progetto.  
  
 [Salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Viene descritto come rendere persistenti i dati in un file di progetto e come utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per mantenere i dati nel file di progetto tra i livelli di aggregazione sottotipo di progetto.  
  
 [Interfaccia utente delle proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)  
 Viene descritto come sottotipi di progetto possono modificare il progetto **pagine delle proprietà** la finestra di dialogo.  
  
 [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fornisce informazioni su come sottotipi di progetto usare Extender di automazione per estendere il modello a oggetti di automazione.  
  
 [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Viene descritto come aggiungere elementi per il **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)  
 Viene illustrato un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo nel file di progetto con il Framework di pacchetto gestito (MPF).  
  
 [Gestione della distribuzione specializzata](../../extensibility/internals/handling-specialized-deployment.md)  
 Viene illustrato come sottotipi di progetto possono fornire il comportamento della distribuzione specializzato mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia.  
  
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)  
 Descrive l'aggiunta e rimozione di pagine delle proprietà in Progettazione progetti.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti che descrivono dettagliatamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti.