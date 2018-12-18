---
title: Salvataggio di un documento personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2b19c6ba222644bc9d5fb97874f50bf6a6aa59d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
Gli handle di ambiente di **salvare**, **Salva con nome**, e **Salva tutto** comandi. Quando un utente fa clic **salvare**, **Salva con nome**, **o Salva tutto** sul **File** menu o chiude la soluzione, pertanto il comando Salva tutto, le operazioni seguenti si verifica.  
  
 ![Salvataggio Editor Customer](../../extensibility/internals/media/private.gif "privato")  
Salvare, Salva con nome e un editor personalizzato di gestione del comando Salva tutto  
  
 Questa procedura è descritta nei passaggi seguenti:  
  
1.  Per il **salvare** e **Salva con nome** comandi, nell'ambiente viene utilizzato il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servizio per determinare la finestra del documento attivo e pertanto gli elementi che devono essere salvati. Una volta che è nota la finestra del documento attivo, l'ambiente trova il puntatore di gerarchia e l'identificatore dell'elemento (ID elemento) per il documento della tabella document in esecuzione. Per ulteriori informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
     Per il comando Salva tutto l'ambiente utilizza le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.  
  
2.  Quando la soluzione riceve un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati (vale a dire le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio).  
  
3.  Su ogni elemento nella selezione, la soluzione utilizza l'indicatore di misura di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il comando di menu Salva deve essere abilitato. Se uno o più elementi sono dirty, quindi viene attivato il comando Salva. Se la gerarchia utilizza un editor standard, i delegati di gerarchia per l'esecuzione di query dirty stato all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo.  
  
4.  Ogni elemento selezionato è stato modificato, la soluzione utilizza l'indicatore di misura di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.  
  
     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. Di conseguenza, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.  
  
    > [!NOTE]
    >  Se si implementa la propria persistenza, assicurarsi di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodo per risparmiare tempo. Questo metodo consente di assicurarsi che è possibile salvare il file (ad esempio, il file non è in sola lettura).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)