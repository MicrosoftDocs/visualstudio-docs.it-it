---
title: "Determinazione dello stato del comando con gli assembly di interoperabilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b7b695288bec904e1e576f9f566944613c97f31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinazione dello stato del comando con gli assembly di interoperabilità
Un pacchetto VSPackage deve tenere traccia dello stato dei comandi che è possibile gestire. L'ambiente non può determinare quando un comando di gestione all'interno del pacchetto VSPackage diventa abilitato o disabilitato. È responsabilità di un VSPackage per informare l'ambiente sugli stati di comando, ad esempio, lo stato di generale i comandi come **Taglia**, **copia**, e **Incolla**.  
  
## <a name="status-notification-sources"></a>Origini di notifica di stato  
 L'ambiente riceve informazioni sui comandi tramite VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo, che fa parte dell'implementazione del pacchetto VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo di VSPackage in due condizioni:  
  
-   Quando un utente apre un menu principale o un menu di scelta rapida (pulsante destro del mouse), l'ambiente è stato eseguito il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo su tutti i comandi di menu per determinare il proprio stato.  
  
-   Quando il pacchetto VSPackage richiede che l'ambiente di aggiornare l'interfaccia utente (UI). Questo errore si verifica come i comandi che sono attualmente visibili all'utente, ad esempio il **Taglia**, **copia**, e **Incolla** sulla barra degli strumenti standard di raggruppamento, diventano abilitati e disabilitati risposta alle azioni dell'utente e di contesto.  
  
 Poiché la shell ospita più pacchetti VSPackage, se sono stati richiesti per eseguire il polling ogni VSPackage per determinare lo stato del comando eccessivamente sarebbero negativamente sulle prestazioni della shell. Al contrario, il pacchetto VSPackage deve notificare attivamente l'ambiente quando cambia la relativa interfaccia utente al momento della modifica. Per ulteriori informazioni sulla notifica di aggiornamento, vedere [aggiornamento dell'interfaccia utente](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Stato di errore di notifica  
 Errore di un VSPackage per notificare l'ambiente di un cambiamento di stato del comando è possibile inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi i contesto o i menu dei comandi di menu può essere inserito su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu di menu o nel contesto non è sufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)