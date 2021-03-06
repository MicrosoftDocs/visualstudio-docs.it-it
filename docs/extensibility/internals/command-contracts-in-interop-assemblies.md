---
title: Contratti di comando negli assembly di interoperabilità | Microsoft Docs
description: Informazioni sul contratto di base per la gestione dei comandi tramite l'interfaccia Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36c757faacb7fe3193f9acbbd040468f66b0623a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086053"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratti di comando negli assembly di interoperabilità
Il contratto di base per la gestione dei comandi tramite l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia è che l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo per determinare se il comando è supportato e, se è supportato, per determinare lo stato e il testo. Quindi, l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per eseguire il comando.

 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene gestito in modo identico per tutti i comandi. Ulteriori comunicazioni, se necessario, ad esempio con elenchi a discesa, vengono gestite chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo con i parametri appropriati. L'interpretazione di questi parametri dipende dal comando specificato.

 Se la destinazione del comando restituisce valori nel parametro di output, il chiamante è sempre responsabile di liberare tutte le risorse allocate. Poiché questo parametro è una variante, la cancellazione della variante libera le risorse.

 Nei casi in cui i comandi devono funzionare all'interno di una finestra della gerarchia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> è necessario usare l'interfaccia. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia ha un contratto simile con metodi simili: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing di comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementazione del comando](../../extensibility/internals/command-implementation.md)
