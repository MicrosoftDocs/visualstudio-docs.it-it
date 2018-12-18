---
title: Progetti di annidamento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="nesting-projects"></a>Progetti di annidamento
Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto di Visual Studio possono consentono di raggruppare tipi simili di insieme di progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando *progetto nidificazione*. Ad esempio, il progetto di modello Enterprise utilizza progetti annidati per i progetti di gruppo in categorie. Progetti di facciata business, i progetti di interfaccia utente Web e così via vengono raggruppati in una categoria.  
  
 In questo scenario non è alcun limite al numero di progetti, che lo sviluppatore può nidificati sotto ogni progetto padre, anche se lo sviluppatore può specificare a livello di codice i limiti. Questo tipo di raggruppamento può essere effettuato anche ricorsivo, nel qual caso i progetti dello stesso tipo come progetto figlio possono essere nidificati sotto l'elemento figlio diventano un sottoprogetto del figlio, che è un sottoprogetto del padre.  
  
 Nidificazione di progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È necessario scrivere il codice per abilitare l'annidamento e sottoprogetto annidamento all'interno dei progetti figlio. Il progetto padre è un pacchetto VSPackage speciale, o tipo di progetto creato e registrato con un proprio GUID che include il codice necessario per implementare la nidificazione di progetto.  
  
 Nell'esempio c# Example.Nested Project, è possibile trovare un esempio di progetti annidati.  
  
## <a name="nested-projects-example"></a>Esempio di progetti annidati  
 ![Annidati Esplora progetti](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
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