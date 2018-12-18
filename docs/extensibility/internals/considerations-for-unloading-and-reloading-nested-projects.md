---
title: Considerazioni per scaricare e ricaricare annidati progetti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd45ebf8be2732cded5c84f18338f104b76840cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerazioni per scaricare e ricaricare progetti annidati
Quando si implementano i tipi di progetto annidato, è necessario eseguire passaggi aggiuntivi quando si scarica e ricaricare i progetti. Per notificare correttamente listener per gli eventi della soluzione, è necessario aumentare in modo corretto il `OnBeforeUnloadProject` e `OnAfterLoadProject` eventi.  
  
 Un motivo per cui è necessario generare questi eventi in questo modo è che non si desidera controllo del codice sorgente (SCC) per eliminare gli elementi dal server e quindi aggiungerli nuovamente come qualcosa di nuovo se è presente un `Get` dell'operazione di controllo del codice sorgente. In tal caso, un nuovo file verranno caricato fuori controllo del codice sorgente ed è necessario scaricare e ricaricare tutti i file nel caso in cui sono diversi. Chiamate di controllo del codice sorgente `ReloadItem`. L'implementazione di tale chiamata consiste nell'eliminare il progetto e ricrearlo nuovamente implementando `IVsFireSolutionEvents` chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject`. Quando si esegue questa implementazione, il controllo del codice sorgente viene informato che il progetto è stato temporaneamente eliminato e aggiunto nuovamente. Di conseguenza, il controllo del codice sorgente non è compatibile con il progetto come se il progetto è stato effettivamente eliminato dal server e quindi aggiunto nuovamente.  
  
## <a name="reloading-projects"></a>Ricaricamento di progetti  
 Per supportare il ricaricamento di progetti annidati, si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Nell'implementazione di `ReloadItem`, si chiudere progetti annidati e quindi ricrearli.  
  
 In genere quando un progetto è stato ricaricato, l'IDE genera il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventi. Tuttavia, per i progetti annidati che verranno eliminati e quindi ricaricati, il progetto principale avvia il processo, non l'IDE. Poiché il progetto principale non genera eventi di soluzione e l'IDE non dispone di informazioni sull'inizializzazione del processo, gli eventi non vengono generati.  
  
 Per gestire questo processo, le chiamate di progetto padre `QueryInterface` sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfaccia disattivato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfaccia. `IVsFireSolutionEvents`sono disponibili funzioni che indicano l'IDE per generare il `OnBeforeUnloadProject` evento per scaricare il progetto annidato e quindi generare il `OnAfterLoadProject` evento di ricaricare il progetto stesso.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)