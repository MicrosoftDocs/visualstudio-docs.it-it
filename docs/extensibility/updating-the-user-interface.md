---
title: Aggiornamento dell'interfaccia utente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bea4f89d2894344069b8aa5b3037bd00b973a40e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="updating-the-user-interface"></a>Aggiornamento dell'interfaccia utente
Dopo aver implementato un comando, è possibile aggiungere codice per aggiornare l'interfaccia utente con lo stato dei nuovi comandi.  
  
 In una tipica applicazione Win32, il set di comandi può eseguire il polling in modo continuo e lo stato di singoli comandi può essere modificato come le visualizza all'utente. Tuttavia, poiché il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell può ospitare un numero illimitato di VSPackage, polling esteso può compromettere la velocità di risposta, in particolare il polling in assembly di interoperabilità tra codice gestito e COM.  
  
### <a name="to-update-the-ui"></a>Per aggiornare l'interfaccia utente  
  
1.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia può essere ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> del servizio, come indicato di seguito.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Se il parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è diverso da zero (`TRUE`), quindi l'aggiornamento viene eseguito in modo sincrono e immediatamente. È consigliabile passare zero (`FALSE`) per questo parametro garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela o può ridurre le prestazioni. Per ulteriori informazioni sui flag di comando, vedere il [comando Flag elemento](../extensibility/command-flag-element.md) documentazione.  
  
    -   Nei pacchetti VSPackage che ospitano un controllo ActiveX utilizzando il modello di attivazione sul posto in una finestra, potrebbe essere più opportuno utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo nel <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia sono funzionalmente equivalenti. Entrambi provocano l'ambiente di eseguire nuovamente query sullo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Al contrario, un aggiornamento viene posticipato fino a quando il tempo di inattività. La shell memorizza nella cache lo stato del comando per garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela perché può ridurre le prestazioni.  
  
         Si noti che è possibile ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia chiamando il `QueryInterface` metodo su un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> dell'oggetto o per ottenere l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../extensibility/internals/command-implementation.md)