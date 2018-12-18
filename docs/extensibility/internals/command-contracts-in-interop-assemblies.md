---
title: "Comando contratti negli assembly di interoperabilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d32a49d780f6ae7929f1442ee70a8085724ca6e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="command-contracts-in-interop-assemblies"></a>Comando contratti negli assembly di interoperabilità
Il contratto di base per la gestione dei comandi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia è che l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo per determinare se il comando è supportato e, se supportato, per determinare il relativo stato e testo. Quindi, l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per eseguire il comando.  
  
 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene gestito in modo identico per tutti i comandi. Le ulteriori comunicazioni, se necessario (ad esempio, con gli elenchi a discesa) sono gestita chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (metodo) con i parametri appropriati. L'interpretazione di questi parametri dipende dal comando specificato.  
  
 Se la destinazione del comando restituisce i valori nel parametro di output, il chiamante è sempre responsabile per liberare le risorse che sono state allocate. Poiché questo parametro è una variante, deselezionando la variante libera le risorse.  
  
 Nei casi in cui i comandi devono funzionare all'interno di una finestra di gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> necessario utilizzare l'interfaccia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia dispone di un contratto simile con metodi simili: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi in VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)