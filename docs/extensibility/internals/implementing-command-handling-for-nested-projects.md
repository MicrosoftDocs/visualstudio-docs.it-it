---
title: Implementazione di gestione dei comandi per annidati progetti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4ed9efab34a51bdfaacea1773a33637437b2ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementazione di gestione dei comandi per progetti annidati
L'IDE è possibile passare i comandi che vengono passati tramite la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfacce per i progetti nidificati o progetti padre è possono filtrare o ignorare i comandi.  
  
> [!NOTE]
>  È possibile filtrare solo i comandi in genere gestiti dal progetto principale. I comandi come **compilare** e **Distribuisci** che vengono gestiti dall'IDE non può essere filtrato.  
  
 I passaggi seguenti descrivono il processo per implementare la gestione dei comandi.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-implement-command-handling"></a>Per implementare la gestione dei comandi  
  
1.  Quando l'utente seleziona un progetto annidato o un nodo in un progetto annidato:  
  
    1.  Le chiamate a IDE il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo.  
  
     oppure  
  
    1.  Se il comando ha avuto origine in una finestra di gerarchia, ad esempio un comando di menu di scelta rapida in Esplora soluzioni, l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodo padre del progetto.  
  
2.  Il progetto principale può esaminare i parametri da passare al `QueryStatus`, ad esempio `pguidCmdGroup` e `prgCmds`, per determinare se il progetto principale deve filtrare i comandi. Se il progetto principale viene implementato per filtrare i comandi, è necessario impostare:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Quindi il progetto principale deve restituire `S_OK`.  
  
     Se il progetto principale non filtra il comando, metodo deve restituire `S_OK`. In questo caso, l'IDE automaticamente indirizza il comando al progetto figlio.  
  
     Il progetto principale non è necessario indirizzare il comando al progetto figlio. L'IDE consente di eseguire questa attività...  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)