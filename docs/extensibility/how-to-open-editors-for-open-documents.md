---
title: 'Procedura: apertura degli editor di documenti aperti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4c6321644cb59f55ad1335249aec5b071aef4ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: apertura degli editor di documenti aperti
Prima di una finestra del documento viene aperto un progetto, il progetto prima di tutto necessario determinare se il file è già aperto nella finestra del documento per un altro editor. Il file è possibile aprire in un editor specifico del progetto o uno degli editor standard registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Aprire un Editor specifico del progetto  
 Utilizzare la procedura seguente per aprire un editor specifico del progetto per un file che è già aperto.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file aperto  
  
1.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Questa chiamata restituisce puntatori a gerarchia del documento, elemento della gerarchia e cornice della finestra, se appropriato.  
  
2.  Se il documento è aperto, il progetto deve verificare se esiste solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione del documento.  
  
    -   Se esiste un oggetto visualizzazione del documento e questa vista è per una gerarchia diversa o un elemento della gerarchia, il progetto utilizza il puntatore alla cornice della finestra della vista per resurface finestra esistente.  
  
    -   Se esiste un oggetto visualizzazione del documento e questa visualizzazione è disponibile per la stessa gerarchia e l'elemento della gerarchia, il progetto può aprire una seconda vista se è possibile collegare all'oggetto dati documento sottostante. In caso contrario, il progetto deve utilizzare il puntatore alla cornice della finestra della vista per resurface finestra esistente.  
  
    -   Se esiste l'oggetto dati del documento, solo il progetto deve determinare se è possibile utilizzare l'oggetto dati del documento per la visualizzazione. Se l'oggetto dati del documento è compatibile, completato i passaggi descritti in [aprire un Editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Se l'oggetto dati del documento non è compatibile, all'utente che indica che il file è attualmente in uso deve essere visualizzato un errore. Questo errore deve essere visualizzato solo in casi temporanei, ad esempio quando un file compilato allo stesso tempo l'utente sta tentando di aprire il file utilizzando un editor diverso di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di testo di base. L'editor di testo core possibile condividere l'oggetto dati del documento con il compilatore.  
  
3.  Se il documento non è aperto, poiché non esiste alcun oggetto dati del documento o un oggetto visualizzazione del documento, completare i passaggi in [aprire un Editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Aprire un Editor Standard  
 Utilizzare la procedura seguente per aprire un editor standard per un file che è già aprire.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard per un file aperto  
  
1.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Questo metodo verifica innanzitutto che il documento non è già aperto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Se il documento è già aperto, la finestra dell'editor è riapparire.  
  
2.  Se il documento non è aperto, quindi completare i passaggi in [procedura: aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: apertura degli editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: Aprire gli editor standard](../extensibility/how-to-open-standard-editors.md)