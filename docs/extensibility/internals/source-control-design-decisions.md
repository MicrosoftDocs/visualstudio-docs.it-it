---
title: Decisioni di progettazione di controllo dell'origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4c1a512e104a092ae98ac86dc5e731fd1732aa33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-design-decisions"></a>Decisioni di progettazione di controllo di origine
Durante l'implementazione di controllo del codice sorgente, è necessario considerare le seguenti decisioni di progettazione per i progetti.  
  
## <a name="will-information-be-shared-or-private"></a>Informazioni sarà condiviso o privato?  
 La decisione di progettazione più importante, che è possibile apportare è quali informazioni sono condivisibili e cosa è privata. Ad esempio, l'elenco di file per il progetto è condiviso, ma all'interno dell'elenco di file, alcuni utenti potrebbero essere necessario disporre di file privati. Le impostazioni del compilatore sono condivisi, ma il progetto di avvio è in genere privato. Le impostazioni sono puramente condiviso, condiviso con un override o esclusivamente privati. Per impostazione predefinita, gli elementi personali, ad esempio utente soluzione opzioni file (suo Solution), non vengono controllati in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Assicurarsi di archiviare informazioni riservate nel file privati, ad esempio il file con estensione suo, o un file privato specifico, ad esempio, creare un. file csproj per Visual c# o. vbproj per Visual Basic.  
  
 Questa decisione è gratis e può essere fatta in un singolo elemento per elemento.  
  
## <a name="will-the-project-include-special-files"></a>Il progetto includerà file speciali?  
 Un'altra importante decisione di progettazione è che la struttura del progetto utilizzi file speciali. File speciali sono nascosti i file che sono visibili in Esplora soluzioni e di archiviazione ed estrazione finestre sottostanti. Se si utilizzano file speciali, attenersi alle seguenti indicazioni:  
  
1.  Non associare file speciale con il nodo radice del progetto, vale a dire, con il progetto file stesso. File di progetto deve essere un singolo file.  
  
2.  Quando di aggiunto, rimosso o rinominati in un progetto, i file speciali <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> eventi devono essere generati con il set di flag che indica i file sono file speciali. Questi eventi vengono chiamati dall'ambiente in risposta al progetto chiamata appropriata <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metodi.  
  
3.  Quando il progetto o un editor chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> per un file, i file speciali associati a tale file non sono automaticamente estratti. Passare i file speciali in insieme al file padre. L'ambiente rileverà la relazione tra tutti i file che vengono passati e nascondere in modo appropriato i file speciali nell'interfaccia utente di estrazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)