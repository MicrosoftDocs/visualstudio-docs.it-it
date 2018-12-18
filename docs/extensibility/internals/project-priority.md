---
title: "Priorità di progetto | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ae692249ea952970b096825c8f6968158eb2f17f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-priority"></a>Priorità del progetto
In genere, un elemento di progetto è un membro di un solo progetto nella soluzione. Pertanto, l'IDE può facilmente determinare quale progetto viene utilizzato per aprire l'elemento. Tuttavia, se un elemento è un membro di più di un progetto, l'IDE Usa una combinazione di priorità per determinare il progetto migliore per aprire l'elemento.  
  
 Nell'elenco seguente viene illustrato lo schema di priorità di progetto:  
  
-   Le chiamate a IDE il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodo per ogni progetto nella soluzione per determinare se il documento è un membro di tale progetto.  
  
-   Se il documento è un membro del progetto, il progetto risponde con una priorità di progetto viene assegnata in base alla relativa funzionalità di gestione di tale documento. Ad esempio, un progetto in linguaggio risponde con una priorità per i file di origine del linguaggio, ma risponde con una priorità più bassa per un tipo di file non riconosciuto che non viene usato come parte del processo di compilazione.  
  
-   I progetti che includono l'editor personalizzato, specifico del progetto o le finestre di progettazione per un documento di inoltre ricevano una priorità alta.  
  
-   Il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione fornisce i valori di priorità il documento.  
  
-   Il progetto che specifica la priorità più alta viene fornito il contesto di aprire il documento. Se i due progetti di restituiscono i valori di uguale priorità, il progetto attivo è preferito. Se nessun progetto nella soluzione risponde che è possibile aprire il documento, l'IDE inserisce il documento nel progetto file esterni. Per ulteriori informazioni, vedere [progetto file esterni](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Progetto file esterni](../../extensibility/internals/miscellaneous-files-project.md)   
 [Procedura: apertura degli editor di documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)