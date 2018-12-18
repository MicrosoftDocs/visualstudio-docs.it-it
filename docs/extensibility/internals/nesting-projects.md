---
title: Progetti di annidamento | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b91f9dc00b9130f2c239bd3254f78376bc0fdf3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="nesting-projects"></a>Progetti di annidamento
Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto di Visual Studio possono consentono di raggruppare tipi simili di insieme di progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando *progetto nidificazione*. Ad esempio, il progetto di modello Enterprise utilizza progetti annidati per i progetti di gruppo in categorie. Progetti di facciata business, i progetti di interfaccia utente Web e così via vengono raggruppati in una categoria.  
  
 In questo scenario non è alcun limite al numero di progetti, che lo sviluppatore può nidificati sotto ogni progetto padre, anche se lo sviluppatore può specificare a livello di codice i limiti. Questo tipo di raggruppamento può essere effettuato anche ricorsivo, nel qual caso i progetti dello stesso tipo come progetto figlio possono essere nidificati sotto l'elemento figlio diventano un sottoprogetto del figlio, che è un sottoprogetto del padre.  
  
 Nidificazione di progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È necessario scrivere il codice per abilitare l'annidamento e sottoprogetto annidamento all'interno dei progetti figlio. Il progetto padre è un pacchetto VSPackage speciale, o tipo di progetto creato e registrato con un proprio GUID che include il codice necessario per implementare la nidificazione di progetto.  
  
 Nell'esempio c# Example.Nested Project, è possibile trovare un esempio di progetti annidati.  
  
## <a name="nested-projects-example"></a>Esempio di progetti annidati  
 ![Soluzione di progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Esempio di progetti annidati  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerazioni per scaricare e ricaricare progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementazione di gestione dei comandi per progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Il filtro nella finestra di dialogo AddItem per progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)