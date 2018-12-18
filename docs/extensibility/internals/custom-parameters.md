---
title: Parametri personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17a629c2d93bb5e91fb301d4da9dca825e5b8917
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="custom-parameters"></a>Parametri personalizzati
Parametri personalizzati controllano il funzionamento di una procedura guidata dopo l'avvio di una procedura guidata. Un file VSZ correlati fornisce una matrice di parametri definiti dall'utente che vengono inserite dall'ambiente di sviluppo integrato (IDE) e passato alla procedura guidata come una matrice di stringhe quando viene avviata la procedura guidata. La procedura guidata, quindi, analizza la matrice di stringhe e utilizza le informazioni di controllo del funzionamento effettivo della procedura guidata. In questo modo, una procedura guidata può personalizzare la funzionalità in base al contenuto del file vsz.  
  
 Parametri di contesto, definiscono invece, lo stato del progetto quando viene avviata la procedura guidata. Per ulteriori informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
 Ecco un esempio di un file VSZ con parametri personalizzati:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L'autore del file VSZ aggiunge i valori dei parametri. Quando un utente seleziona **nuovo progetto** o **Aggiungi nuovo elemento** dal menu File o facendo clic su un progetto in **Esplora**, l'IDE raccoglie questi valori in una matrice di stringhe. L'IDE chiama quindi il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag set e le chiamate di progetto di <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodo che è responsabile dell'esecuzione della procedura guidata e la restituzione del risultato.  
  
 La procedura guidata è responsabile dell'analisi la matrice di stringhe e le stringhe che opera in modo appropriato. In questo modo, tramite l'implementazione di parametri personalizzati è possibile creare una procedura guidata che viene eseguita una varietà di funzioni. In altre parole, una procedura guidata potrebbe avere tre file VSZ diversi. Ogni file passa diversi set di parametri personalizzati per controllare il comportamento della procedura guidata in diverse situazioni.  
  
 Per ulteriori informazioni, vedere [guidata (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)