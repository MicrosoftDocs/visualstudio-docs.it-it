---
title: Persistenza del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b85bb6155ca25abec67b582dc4d877dbd8290501
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-persistence"></a>Persistenza del progetto
La persistenza è una considerazione di progettazione chiave per il progetto. La maggior parte dei progetti utilizzano gli elementi di progetto che rappresentano file; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta anche i progetti i cui dati sono non basate su file. Entrambi i file di proprietà del progetto e il file di progetto devono essere resa persistente. L'IDE consente di configurare il progetto per salvare se stesso o un elemento di progetto.  
  
 Modelli per i progetti vengono passati per la factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi di progetto in base ai requisiti del tipo di progetto specifico. Questi modelli in un secondo momento possono essere salvati come file di progetto e gestiti dall'IDE tramite la soluzione. Per ulteriori informazioni, vedere [la creazione di istanze da utilizzando progetto factory dei progetti](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [soluzioni](../../extensibility/internals/solutions.md).  
  
 Elementi di progetto possono essere basata su file o non basate su file:  
  
-   Gli elementi basati su file possono essere locale o remoto. Nei progetti Web in c#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenute in locale, mentre per mantenere gli stessi file nel sistema remoto.  
  
-   Articoli basati su file è possono salvare gli elementi di un database o nell'archivio.  
  
## <a name="commit-models"></a>Eseguire il commit di modelli  
 Dopo avere deciso in cui si trovano gli elementi del progetto, è necessario scegliere il modello appropriato di commit. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository, è possibile salvare più elementi in una transazione. Per ulteriori informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Per determinare le estensioni di file, progetti di implementano il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia che fornisce informazioni sull'abilitazione di un oggetto client implementare il **Salva con nome** la finestra di dialogo, ovvero, ovvero per riempire il **Salva con nome**  elenco a discesa elencare e gestire l'estensione del nome file iniziale.  
  
 Le chiamate a IDE il `IPersistFileFormat` interfaccia nel progetto per indicare che il progetto deve essere mantenuto il relativo progetto elementi a seconda dei casi. Pertanto, l'oggetto proprietario di tutti gli aspetti relativi file e il formato. Ciò include il nome del formato dell'oggetto.  
  
 Nel caso in cui gli elementi non sono file, `IPersistFileFormat` è ancora come non-basate su file gli elementi sono persistenti. File di progetto, ad esempio file vbp per [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetti o vcproj file per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti, deve inoltre essere resa persistente.  
  
 Per salvare le azioni, l'IDE esamina tabella document (RDT) in esecuzione e la gerarchia passa i comandi per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfacce. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> metodo viene implementato per determinare se l'elemento è stato modificato. Se l'elemento include, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metodo viene implementato per salvare l'elemento modificato.  
  
 I metodi di `IVsPersistHierarchyItem2` interfaccia vengono utilizzati per determinare se un elemento può essere ricaricato e, se l'elemento può essere ricaricarlo. Inoltre, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metodo può essere implementato per generare gli elementi modificati essere eliminata senza essere salvato.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)