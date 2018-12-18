---
title: Utilizzo di RDT_ReadLock | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c13d9255442459c884379e83b619e1f73a1c2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="rdtreadlock-usage"></a>Utilizzo di RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>è un flag che fornisce la logica per il blocco di un documento nell'esecuzione documento tabella (RDT), che corrisponde all'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio. Questo flag determina quando vengono aperti i documenti e se un documento è visibile nell'interfaccia utente o mantenute in modo invisibile in memoria.

In genere, si utilizzerebbe <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> quando una delle operazioni seguenti è vera:

- Quando si desidera aprire un documento in modo invisibile e di sola lettura, ma non è ancora stato stabilito che <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> deve i proprietari.

- Quando si desidera che l'utente verrà richiesto di salvare un documento che è stato aperto in modo invisibile prima che l'utente viene visualizzato nell'interfaccia utente e quindi ha tentato di chiuderlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire i documenti visibili e invisibili

Quando un utente apre un documento nell'interfaccia utente, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietario per il documento deve essere stabilita e un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> flag deve essere impostato. Se non <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietario può essere stabilito, quindi il documento non verrà salvato quando l'utente fa clic **Salva tutto** o chiude l'IDE. Ciò significa che se si apre un documento in modo invisibile in cui viene modificato in memoria e l'utente viene richiesto di salvare il documento in fase di arresto o salvato se **Salva tutto** viene scelto un `RDT_ReadLock` non può essere utilizzato. In alternativa, è necessario utilizzare un `RDT_EditLock` e registrare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> quando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> flag.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock e modifica dei documenti

Il flag precedente indicato indica che l'apertura del documento invisibile genererà il `RDT_EditLock` quando il documento viene aperto dall'utente in un oggetto visibile **DocumentWindow**. In questo caso, viene visualizzata con un **salvare** richiedere quando visibile **DocumentWindow** viene chiuso. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`le implementazioni che usano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> servizio lavoro inizialmente quando solo un `RDT_ReadLock` (ad esempio, quando il documento viene aperto in modo invisibile per analizzare le informazioni) non viene eseguita. In un secondo momento, se il documento deve essere modificato, quindi il blocco viene aggiornato a un "Weak" **RDT_EditLock**. Se l'utente apre quindi il documento in un oggetto visibile **DocumentWindow**, `CodeModel`del debole `RDT_EditLock` viene rilasciato.

Se l'utente chiude il **DocumentWindow** e sceglie **n** quando viene richiesto di salvare il documento aperto, il `CodeModel` implementazione Elimina tutte le informazioni nel documento e riapre il documento da disco in modo invisibile al successivo che ulteriori informazioni sono necessarie per il documento. L'abbastanza particolare di questo comportamento è un'istanza in cui l'utente apre il **DocumentWindow** del documento aperto invisibile, modifica, lo chiude e quindi sceglie **n** quando viene richiesto di salvare il documento. In questo caso, se il documento ha un `RDT_ReadLock`, il documento non viene effettivamente chiuso e il documento modificato rimarrà aperto in modo invisibile in memoria, anche se l'utente ha scelto di non salvare il documento.

Se l'apertura del documento invisibile utilizza un "Weak" `RDT_EditLock`, quindi restituisce il blocco quando l'utente apre il documento visibili e non altri blocchi. Quando l'utente chiude il **DocumentWindow** e sceglie **n** quando viene richiesto di salvare il documento, il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve essere in ascolto per gli eventi RDT tenere traccia di questa occorrenza. La volta successiva che il documento è obbligatorio, il documento deve essere riaperto.