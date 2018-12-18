---
title: Intercettazione di comandi del servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ad7870fcec07db3d4d529b856bc0e2f18006e819
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercettazione di comandi del servizio di linguaggio Legacy
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile disporre i comandi intercetta servizio linguaggio gestire in altro modo la visualizzazione del testo. Ciò è utile per il comportamento specifico del linguaggio che non gestisce la visualizzazione del testo. È possibile intercettare questi comandi mediante l'aggiunta di uno o più filtri dei comandi per la visualizzazione del testo dal servizio di linguaggio.  
  
## <a name="getting-and-routing-the-command"></a>Recupero e il comando di Routing  
 Un filtro è un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto che controlla alcune sequenze di caratteri o i comandi. È possibile associare più di un filtro di comando con una visualizzazione di testo singola. Ogni visualizzazione testo gestisce una catena di comando di filtri. Dopo aver creato un nuovo filtro di comando, aggiungere il filtro alla catena per la visualizzazione di testo appropriato.  
  
 Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiungere il filtro di comando della catena. Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] restituisce un altro filtro di comando a cui è possibile passare i comandi che non consente di gestire il filtro dei comandi.  
  
 Sono disponibili le opzioni seguenti per la gestione dei comandi:  
  
-   Gestire il comando, quindi passare il comando al filtro comando successivo nella catena.  
  
-   Gestire il comando e non passare il comando al filtro comando successivo.  
  
-   Non gestisce il comando e passare il comando al filtro comando successivo.  
  
-   Ignorare il comando. Non viene gestito nel filtro corrente e non passarla filtro successivo.  
  
 Per informazioni sui comandi che deve gestire il servizio di linguaggio, vedere [comandi importanti per i filtri di servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).