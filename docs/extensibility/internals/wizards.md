---
title: Wizards | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 96d91fa687c914f0c3f98c4ddca64a93a5d70d02
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="wizards"></a>Procedure guidate
Dopo aver creato una procedura guidata, in genere da aggiungere per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato (IDE) di ambiente di sviluppo in modo che altri utenti possono utilizzarlo. La procedura Aggiunta guidata viene quindi visualizzata nel **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** finestre di dialogo. Per visualizzare il **Aggiungi nuovo progetto** o **Aggiungi nuovo elemento** finestra di dialogo finestre, fare doppio clic su una soluzione aperta in **Esplora**, scegliere **Aggiungi**, e quindi fare clic su **nuovo progetto** o **nuovo elemento**.  
  
 Procedure guidate possono essere implementate in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per consentire agli utenti di selezionare da una visualizzazione albero di valori disponibili quando viene aperto il **Aggiungi nuovo progetto** la finestra di dialogo o **Aggiungi nuovo elemento** nella finestra di dialogo o quando sono fare doppio clic su un elemento **Esplora**.  
  
 Nella procedura guidata, è possibile fornire la possibilità di localizzazione il nome di un nuovo progetto o ites ed è possibile determinare l'icona che gli utenti visualizzeranno quando si seleziona la procedura guidata. È inoltre possibile controllare l'ordine in cui vengono visualizzati nuovi elementi relativo altri elementi disponibili; gli elementi non debbano essere organizzati in ordine alfabetico.  
  
 È inoltre possibile fornire una procedura guidata che viene avviato in modo diverso, in base ai parametri personalizzati che vengono passati alla procedura guidata quando viene aperto.  
  
 Negli argomenti di questa sezione viene illustrato i file che implementano per fare in modo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** finestre di dialogo per visualizzare l'elenco tra le procedure guidate disponibili e i modelli, una procedura guidata e i requisiti che deve essere soddisfatti per non operi correttamente nell'IDE di una procedura guidata.  
  
## <a name="in-this-section"></a>In questa sezione  
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Fornisce una panoramica del modello di quali file description di directory e funzionamento nell'IDE per la visualizzazione di cartelle, file VSZ della procedura guidata e i file di modello che sono associati a un progetto nelle finestre di dialogo.  
  
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Viene illustrato l'IDE di avvio di procedure guidate e sono elencate le tre parti del file vsz.  
  
 [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Viene descritto il `IDTWizard` interfaccia che devono implementare le procedure guidate per funzionare nell'IDE.  
  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)  
 Illustra le modalità di implementazione delle procedure guidate e cosa si verifica quando l'IDE passa i parametri di contesto per l'implementazione.  
  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)  
 Viene illustrato come utilizzare i parametri personalizzati per controllare il funzionamento della procedura guidata dopo aver avviata la procedura guidata.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.  
  
 [Estensione dei progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti e soluzioni per organizzare i file di codice e file di risorse e come implementare il codice sorgente.