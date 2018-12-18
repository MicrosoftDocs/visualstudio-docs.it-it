---
title: Dati del documento e documento della visualizzazione in un editor personalizzato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb445ca70ac74cf2601e9f1035549bb686fca798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dati del documento e visualizzazione del documento in un editor personalizzato
Un editor personalizzato è costituito da due parti: un oggetto dati del documento e un oggetto visualizzazione del documento. Come suggeriscono i nomi, l'oggetto dati del documento rappresenta i dati di testo da visualizzare e l'oggetto visualizzazione del documento (o "view") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.  
  
## <a name="document-data-object"></a>Oggetto dati del documento  
 Un oggetto dati del documento è una rappresentazione di dati di testo nel buffer di testo. È un oggetto COM che consente di archiviare il testo del documento e altre informazioni, gestisce la persistenza di documento e Abilita più visualizzazioni dei dati. Per altre informazioni, vedere  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> e [finestre dei documenti](../extensibility/internals/document-windows.md).  
  
 Editor personalizzati e finestre di progettazione è possibile scegliere di usare il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto o i propri buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più viste e fornisce interfacce eventi che consentono di gestire più viste.  
  
## <a name="document-view-object"></a>Oggetto visualizzazione del documento  
 Una finestra che consente di visualizzare codice e altro testo è noto come un documento o una vista. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui viene visualizzato il testo in una singola finestra o una vista più, in cui viene visualizzato il testo in più di una finestra. La scelta dipende dall'applicazione. Ad esempio, se è necessario side-by-side di modifica, selezionare visualizzazione di più. Ogni visualizzazione è associata a una voce in integrato dell'ambiente di sviluppo (IDE) in esecuzione la tabella document (RDT). Windows vista appartiene a un progetto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.  
  
 Se l'editor supporta più viste di un oggetto dati del documento, quindi i dati del documento e gli oggetti di visualizzazione documento devono essere separati. In caso contrario, essi possono essere raggruppati. Per ulteriori informazioni, vedere [di supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
 L'IDE notifica viste sugli eventi (ad esempio, quando una soluzione contenente un documento viene chiuso) associando un identificatore dell'elemento (ID elemento) per ogni voce della tabella document in esecuzione. Per ulteriori informazioni, vedere [tabella documenti in esecuzione](../extensibility/internals/running-document-table.md).  
  
 Sono disponibili due opzioni per la creazione di una visualizzazione per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la vista è ospitata in una finestra con un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la vista è ospitata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> viene implementato per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [attivazione sul posto](../extensibility/in-place-activation.md). Per informazioni sul modello di incorporamento semplificato, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Semplificato incorporamento](../extensibility/simplified-embedding.md)   
 [Procedura: collegare viste per documentare i dati](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestione dei documenti blocco titolare](../extensibility/document-lock-holder-management.md)   
 [Singole e multi-scheda viste](../extensibility/single-and-multi-tab-views.md)   
 [Salvataggio di un documento Standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenza e la tabella Document in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinazione di un File in un progetto che verrà aperto l'Editor](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Factory editor](../extensibility/editor-factories.md)