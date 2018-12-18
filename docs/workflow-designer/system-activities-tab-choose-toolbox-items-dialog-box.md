---
title: Scheda System. Activities, scegliere la finestra di dialogo di elementi della casella degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ba4078a903c1e30b968928e13c8d160c898bbf0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Scheda System.Activities, finestra di dialogo Scegli elementi della Casella degli strumenti
Questa scheda della finestra di **Scegli elementi della casella degli strumenti** la finestra di dialogo Visualizza un elenco di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] attività, modelli e gli elementi disponibili. Per visualizzare l'elenco, selezionare **Scegli elementi della casella degli strumenti** dal **strumenti** menu o facendo clic con il **della casella degli strumenti** e selezionando **Scegli elementi**per visualizzare il **Scegli elementi della casella degli strumenti** la finestra di dialogo e quindi selezionare il **System. Activities** scheda. Predefinita, l'elenco contiene le attività del flusso di lavoro dagli assembly System. Activities System.ServiceModel.Activities e System.Activities.Core.Presentation. Tuttavia, solo fornito dal sistema attività visualizzate e le attività aggiunte mediante altri assembly visualizzati di **della casella degli strumenti** sono selezionate per impostazione predefinita. Aggiunti di recente le attività vengono controllate automaticamente e vengono visualizzati di **della casella degli strumenti** quando fa clic su **OK** nella finestra di dialogo. Inoltre, questi elementi vengono visualizzati nel **della casella degli strumenti** in una nuova categoria che corrisponde allo spazio dei nomi in cui si trova l'attività di elemento o il modello.  
  
> [!WARNING]
>  Se si prova ad aggiungere un assembly che non contiene attività del flusso di lavoro, viene visualizzata una finestra di errore in cui si segnala che l'assembly non contiene attività.  
  
 Questa finestra di dialogo è indipendente dal progetto e pertanto il **System. Activities** scheda continua a presentarsi in XAML autonomo o un tipo di progetto senza flusso di lavoro.  
  
 Il filtro viene applicato in ogni scheda. Ciò significa non è possibile aggiungere le attività del flusso di lavoro tramite il **componente .NET** scheda. Devono essere aggiunti tramite il **System. Activities** sulla stessa scheda.  
  
 È possibile deselezionare tutti gli elementi non si desidera vedere nel **della casella degli strumenti** da questa finestra di dialogo oppure in alternativa, è possibile eseguire quindi l'uso il **eliminare** voce di menu nel contesto la **della casella degli strumenti** e rimuovere un assembly di riferimento non rimuovere l'elemento di **della casella degli strumenti**.  
  
 Quando si crea un'istanza dell'attività trascinandola e rilasciandola nella finestra di progettazione, si aggiunge automaticamente all'elenco degli assembly di riferimento l'assembly che contiene l'elemento. Se inoltre l'attività fa riferimento a un assembly C, C non viene aggiunto all'elenco di assembly di riferimento. Assembly C deve trovarsi nella Global Assembly Cache o nella stessa directory dell'attività B. Nel caso autonomo, l'assembly deve trovarsi nella GAC o nei percorsi di Probe di VS. È quindi solo possibile trascinare e rilasciare le attività nell'area di progettazione flussi di lavoro.  
  
 **Casella degli strumenti** impostazioni vengono salvate per impostazione predefinita come opzioni utente, pertanto il successivo, quando si apre il **della casella degli strumenti**, viene visualizzato l'elenco delle attività del flusso di lavoro personalizzato. Un effetto collaterale di questo oggetto è che, se sono stati aggiunti gli elementi specifici di dominio per il **della casella degli strumenti** tramite il **Scegli elementi della casella degli strumenti** la finestra di dialogo, è comunque continuare a visualizzare tali elementi quando si lavora un Flusso di lavoro nonché applicazione Console. Se non si desidera visualizzarli, eliminarli utilizzando il menu di scelta rapida oppure deselezionarli il **Scegli elementi della casella degli strumenti** la finestra di dialogo come indicato in precedenza.  
  
 Le colonne di questa finestra di dialogo includono le informazioni seguenti:  
  
 Nome  
 Elenca i nomi delle attività del flusso di lavoro attualmente registrate nel computer locale.  
  
 Spazio dei nomi  
 Visualizza la gerarchia dello spazio dei nomi della libreria di classi .NET Framework che definisce la struttura dell'attività.  
  
 Nome assembly  
 Visualizza il nome e la versione dell'assembly .NET Framework che include l'attività.  
  
 Directory  
 Visualizza il percorso dell'assembly .NET Framework che include le attività del flusso di lavoro. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache.  
  
 Per ordinare i componenti elencati, selezionare una delle intestazioni di colonna.