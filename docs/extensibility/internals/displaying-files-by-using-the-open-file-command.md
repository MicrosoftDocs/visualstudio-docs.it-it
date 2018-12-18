---
title: Visualizzazione di file utilizzando il comando Apri File | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b84992dc1803f1eee4fc36d477db1708eb90904
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Visualizzazione di file utilizzando il comando Apri File
I passaggi seguenti descrivono il modo in cui l'IDE gestisce il **Apri File** comando, è disponibile nel **File** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Viene descritta anche la modalità con cui i progetti devono risposta alle chiamate provenienti da questo comando.  
  
 Quando un utente fa clic il **Apri File** comando il **File** dal menu e seleziona un file dal **Apri** si verifica il processo seguente nella finestra di dialogo.  
  
1.  Utilizzando la tabella documenti in esecuzione, l'IDE determina se il file è già aperto in un progetto.  
  
    -   Se il file è aperto, l'IDE riemerga la finestra.  
  
    -   Se il file non è aperto, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> per ogni progetto per determinare quale progetto è possibile aprire il file di query.  
  
        > [!NOTE]
        >  Nell'implementazione del progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, fornire un valore che indica il livello in cui il progetto viene aperto il file di priorità. Vengono forniti valori di priorità nel <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione.  
  
2.  Ogni progetto risponde con un livello di priorità che indica l'importanza viene inserito in corso il progetto per aprire il file.  
  
3.  L'IDE Usa i criteri seguenti per determinare quale progetto viene aperto il file:  
  
    -   Il file verrà aperto il progetto che risponde con la priorità più alta (DP_Intrinsic). Se più di un progetto risponde con la priorità, il progetto prima di rispondere apre il file.  
  
    -   Se non risponde del progetto con la priorità più alta (DP_Intrinsic), ma tutti i progetti risponde con la priorità più bassa, stesso, il progetto attivo apre il file. Se è attivo alcun progetto, il progetto prima di rispondere apre il file.  
  
    -   Se nessun progetto le attestazioni di proprietà del file (DP_Unsupported), il progetto file esterni apre il file.  
  
         Se viene creata un'istanza del progetto file esterni, il progetto risponde sempre con il valore DP_CanAddAsExternal. Questo valore indica che il progetto è possibile aprire il file. Questo progetto viene utilizzato per ospitare i file aperti che non sono presenti in qualsiasi altro progetto. L'elenco di elementi in questo progetto non è persistente; Questo progetto è visibile in **Esplora** solo quando viene utilizzato per aprire un file.  
  
         Se il progetto file esterni non indica che è possibile aprire il file, un'istanza del progetto non è stata creata. In questo caso, l'IDE crea un'istanza del progetto file esterni e indica il progetto per aprire il file.  
  
4.  Non appena l'IDE determina quale progetto viene aperto il file, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo su tale progetto.  
  
5.  Il progetto è quindi possibile aprire il file usando un editor specifico del progetto o un editor standard. Per ulteriori informazioni, vedere [come: gli editor aperti specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md) e [procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)rispettivamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di file tramite l'apertura con il comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: apertura degli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)