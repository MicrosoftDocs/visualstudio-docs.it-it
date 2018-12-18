---
title: Cenni preliminari sulle soluzioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 539ceb45cce6c317ed3723c5006e6d2a77029335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="solutions-overview"></a>Cenni preliminari sulle soluzioni
Una soluzione è un raggruppamento di uno o più progetti che funzionano insieme per creare un'applicazione. Le informazioni di stato e di progetto relativi alla soluzione vengono archiviati in due file di soluzione diversa. Il file di soluzione (sln) è basata su testo e possono essere sottoposti a controllo del codice sorgente e condivisi dagli utenti. Il file della soluzione utente opzione (suo Solution) è binario. Di conseguenza, il file con estensione suo non può essere inserito sotto controllo del codice sorgente e contiene informazioni specifiche dell'utente.  
  
 Qualsiasi pacchetto VSPackage può scrivere in entrambi i tipi di file della soluzione. A causa della natura dei file, esistono due diverse interfacce implementate per scrivere su di esse. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia scrive le informazioni di testo per il file con estensione sln e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia scrive il file con estensione suo flussi binari.  
  
> [!NOTE]
>  Un progetto non è necessario scrivere in modo esplicito una voce per se stesso nel file di soluzione; l'ambiente di gestione che per il progetto. Pertanto, a meno che non si desidera aggiungere contenuto aggiuntivo in modo specifico per il file della soluzione, non è necessario registrare il VSPackage in questo modo.  
  
 Ogni pacchetto VSPackage che supporta la persistenza soluzione utilizza tre interfacce, di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia, che viene implementata dall'ambiente e chiamato dal pacchetto VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, che sono entrambi implementati dal pacchetto VSPackage. Il `IVsPersistSolutionOpts` solo interfaccia deve essere implementata nel caso in cui scrivere il file con estensione suo dal pacchetto VSPackage informazioni private.  
  
 Quando viene aperta una soluzione, il processo seguente viene eseguita.  
  
1.  L'ambiente legge la soluzione.  
  
2.  Se l'ambiente rileva un `CLSID`, carica il pacchetto VSPackage corrispondente.  
  
3.  Se viene caricato un pacchetto VSPackage, l'ambiente chiama `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaccia per l'interfaccia che richiede il pacchetto VSPackage.  
  
    1.  Durante la lettura da un file con estensione sln, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionProps`.  
  
    2.  Durante la lettura da un file con estensione suo, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionOpts`.  
  
 Informazioni specifiche relative all'utilizzo di questi file sono reperibile [soluzione (. File sln)](../../extensibility/internals/solution-dot-sln-file.md) e [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Se si desidera creare una nuova configurazione di soluzione costituito da configurazioni due progetti e l'esclusione di un terzo di compilazione, è necessario utilizzare l'interfaccia utente delle pagine delle proprietà o l'automazione. Non è possibile modificare le configurazioni di manager di compilazione di soluzioni e le relative proprietà direttamente, ma è possibile modificare il gestore di compilazione della soluzione utilizzando la `SolutionBuild` classe da DTE nel modello di automazione. Per ulteriori informazioni sulla configurazione di soluzioni, vedere [configurazione soluzione](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>