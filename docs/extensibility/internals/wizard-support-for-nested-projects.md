---
title: Supporto della procedura guidata per i progetti annidati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757968aabfc256cda37a103d48c8d12f1fc16fa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-support-for-nested-projects"></a>Supporto della procedura guidata per i progetti annidati
Nell'IDE vengono eseguiti due procedure guidate che può implementare il progetto principale per i progetti annidati: il **nuovo progetto** procedura guidata e **Aggiungi elemento** procedura guidata.  
  
 Se un utente avvia il **nuovo progetto** procedura guidata selezionando **Aggiungi progetto** e facendo clic su **nuovo progetto** dal menu File oppure selezionando **Aggiungi** pulsante destro del mouse **nuovo progetto** in Esplora soluzioni, viene eseguito l'IDE di **AddProject** comando e l'implementazione del progetto padre del **AddProject**comando restituisce un file di progetto di modello o un file di procedura guidata (vsz) che include un set di parametri di contesto.  
  
 Analogamente, implementazione di un progetto padre di **AddItem** procedure guidate restituisce un file VSZ che include un set diverso di parametri di contesto.  
  
 Per ulteriori informazioni sulle procedure guidate, vedere [guidata (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parametri di contesto](../../extensibility/internals/context-parameters.md) e [registrazione Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)