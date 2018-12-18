---
title: Hosting di IntelliSense | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9727b6fcbe3c552273ca521e8fd14ab5e5181eb7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="intellisense-hosting"></a>Hosting di IntelliSense
Visual Studio consente l'hosting di IntelliSense. IntellSense hosting consente di fornire IntelliSense per codice che non è ospitato dall'editor di testo di Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilizzo di Hosting di IntelliSense  
 In Visual Studio, qualsiasi codice che ha accesso a un set di completamento e di un buffer di testo può ottenere IntelliSense windows ovunque nell'interfaccia utente (UI). Alcuni scenari di questo esempio sono completamento nel **espressioni di controllo** finestra o nel campo condizione di una finestra delle proprietà del punto di interruzione.  
  
### <a name="implementation-interfaces"></a>Interfacce di implementazione  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualsiasi componente dell'interfaccia utente che ospita le finestre popup IntelliSense deve supportare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia. La visualizzazione del testo dell'editor principale predefinito includa un magazzino <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementazione per mantenere la funzionalità IntelliSense corrente dell'interfaccia. La maggior parte, i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia rappresentano un subset di ciò che viene implementato sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia. Il sottoinsieme include gestione UI IntelliSense, punto di inserimento e la modifica di selezione e funzionalità di sostituzione di testo semplice. Inoltre, il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia consente separato IntelliSense "subject" e "contesto" in modo che venga fornito IntelliSense per oggetti che non esistono direttamente nel buffer di testo che viene utilizzato per il contesto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia provider deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> metodo per consentire a un client determinare il tipo di IntelliSense funzionalità host supporta.  
  
 I flag di host, definiti in [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sono riepilogate di seguito.  
  
|Flag di Host di IntelliSense|Descrizione|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Impostando questo flag del buffer del contesto è in sola lettura e modifica si verifica solo all'interno del testo di oggetto.|  
|IHF_NOSEPERATESUBJECT|Impostazione di questo flag indica che non vi è alcun oggetto IntelliSense separato. L'oggetto esiste nel buffer del contesto, ad esempio nel tradizionale <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense.|  
|IHF_SINGLELINESUBJECT|Impostando questo flag non è soggetto a più righe in grado di supportare, ad esempio una singola riga modifica nel **espressioni di controllo** finestra.|  
|IHF_FORCECOMMITTOCONTEXT|Se questo flag è impostato e il buffer del contesto deve essere aggiornato, l'host Abilita il flag di sola lettura nel buffer del contesto verrà ignorato e modifiche per continuare.|  
|IHF_OVERTYPE|La modifica (in oggetto o il contesto) deve essere eseguita in modalità di sovrascrittura.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Questi metodi di callback vengono chiamati dalla finestra di completamento prima e dopo il testo viene eseguito il commit, per abilitare la pre-elaborazione e post-elaborazione.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interfaccia è una versione generabile condiviso della finestra di completamento standard che viene utilizzata dall'ambiente di sviluppo integrato (IDE). Qualsiasi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfaccia possa implementare rapidamente IntelliSense tramite questa interfaccia completor.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop>