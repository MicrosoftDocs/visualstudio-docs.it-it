---
title: Il filtro nella finestra di dialogo AddItem per progetti annidati | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Il filtro nella finestra di dialogo AddItem per progetti annidati
Quando si visualizza un **AddItem** la finestra di dialogo per un progetto annidato nel progetto padre è possibile controllare quali elementi vengono visualizzati nella finestra di dialogo.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia consente di filtrare i nodi che verrà aggiunto un **AddItem** la finestra di dialogo. Quando il progetto figlio viene visualizzato il **AddItem** nella finestra di dialogo in cui è possibile implementare l'elemento padre di `IVsFilterAddProjectItemDlg` gli elementi dell'interfaccia e filtro, in caso contrario, verrebbero visualizzati nel progetto del bambino.  
  
 Quando i progetti vengono raggruppati dalla funzione in progetti di entità padre specifica, è possibile implementare `IVsFilterAddProjectItemDlg` quando l'utente seleziona **Aggiungi elemento di progetto** nel menu di scelta rapida in un progetto annidato. Implementazione `IvsFilterAddProjectItemDlg displays` progetto solo gli elementi o i file specifico di tale gruppo. Elementi di progetto per altri gruppi vengono filtrati dalla finestra di dialogo, anche se si trovano nella stessa directory.  
  
 Quando un utente apre il **AddItem** per l'oggetto figlio, l'implementazione del progetto padre della finestra di dialogo di `IVsFilterAddProjectItemDlg` interfaccia viene chiamata.  
  
 Il `IVsFilterAddProjectItemDlg` interfaccia può anche implementare il filtro per categoria. Per ulteriori informazioni, vedere [aggiunta di elementi finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrazione Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)