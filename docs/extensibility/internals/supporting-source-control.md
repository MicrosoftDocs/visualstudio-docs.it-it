---
title: Supporto di controllo del codice sorgente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-source-control"></a>Supporto di controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta file estrazioni archiviazioni e altre operazioni di controllo per il progetto o un editor. Come un client di controllo del codice sorgente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è progettato per interagire con un pacchetto di controllo di origine, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], che fornisce l'archiviazione, il controllo delle versioni e funzionalità di controllo per un set di file definito dinamicamente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modello per i pacchetti del controllo del codice sorgente](../../extensibility/internals/model-for-source-control-packages.md)  
 Vengono descritte le interfacce di un tipo di progetto deve implementare per supportare controllo del codice sorgente.  
  
 [Decisioni di progettazione](../../extensibility/internals/source-control-design-decisions.md)  
 Fornisce le domande cui risposte modifica modalità di implementazione di un tipo di progetto.  
  
 [Dettagli di configurazione](../../extensibility/internals/source-control-configuration-details.md)  
 Viene descritto come supporto di controllo del codice sorgente cambia l'implementazione di un tipo di progetto.  
  
 [Ulteriori linee guida per gli editor e progetti](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Illustra le procedure consigliate per i tipi di progetto e di editor.  
  
 [Dettagli di runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Viene descritto come registrare un progetto quando un utente viene aggiunto a un sistema di controllo del codice sorgente.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica all'ambiente o pacchetto di controllo di origine che un file sta per essere modificato in memoria o salvata.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Consente di progetti e le gerarchie di registrarsi con controllo del codice sorgente e ottenere informazioni sullo stato di controllo di origine.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementata in un sistema di progetto per fornire il codice sorgente per il file di progetto e gli elementi di progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilizzato dai progetti per l'ambiente per l'autorizzazione aggiungere, rimuovere o rinominare un file o directory in una soluzione di query.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica ai client delle modifiche apportate al file di progetto o directory.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Fornisce una panoramica dei progetti come blocchi predefiniti di base di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.