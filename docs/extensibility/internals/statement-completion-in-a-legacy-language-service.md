---
title: Completamento delle istruzioni in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7208d38966e2caa9f9510c48c34952742d06c1b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Completamento delle istruzioni in un servizio di linguaggio Legacy
Completamento delle istruzioni è il processo mediante il quale il servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento che hanno hanno avviato l'editor di componenti di base. In questo argomento viene descritto il funzionamento di completamento delle istruzioni e per l'implementazione del servizio di linguaggio.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare il completamento delle istruzioni, vedere [procedura dettagliata: visualizzazione di completamento delle istruzioni](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementing-statement-completion"></a>Implementazione di completamento istruzioni  
 Nell'editor di componenti di base, il completamento delle istruzioni attiva un'interfaccia utente speciale che in modo interattivo consente più facilmente e rapidamente scrittura codice. Consente di completamento delle istruzioni visualizzando oggetti pertinenti o classi quando sono necessari, che consente di evitare di dover ricordare elementi specifici o che sia necessario cercarli in un argomento di riferimento della Guida.  
  
 Per implementare il completamento delle istruzioni, la lingua deve avere un trigger di completamento istruzione, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Usa un operatore punto (.), mentre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utilizza una freccia (->) (operatore). Un servizio di linguaggio è possibile utilizzare più di un trigger per avviare il completamento delle istruzioni. Questi trigger vengono programmati nel filtro del comando.  
  
## <a name="command-filters-and-triggers"></a>Filtri dei comandi e trigger  
 Comandi filtri intercettano le occorrenze del trigger o del trigger. Per aggiungere il filtro dei comandi per la visualizzazione, implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e collegarlo alla visualizzazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo. È possibile utilizzare lo stesso filtro di comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) per tutti gli aspetti del servizio di linguaggio, ad esempio il completamento delle istruzioni, i marcatori di errore e suggerimenti (metodo). Per ulteriori informazioni, vedere [intercettazione di comandi del servizio di linguaggio Legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Quando il trigger viene immesso nell'editor, in particolare, il buffer di testo, quindi chiama il servizio di linguaggio il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> (metodo). In questo modo l'editor visualizzare l'interfaccia utente in modo che l'utente può scegliere tra i candidati di completamento istruzione. Questo metodo è necessario implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> e <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag come parametri. L'elenco degli elementi di completamento viene visualizzata in una casella di scorrimento. L'utente continua a digitare, la selezione nella casella di riepilogo viene aggiornata per riflettere che la corrispondenza più vicina per i caratteri più recente tipizzati. L'editor di componenti di base implementa l'interfaccia utente per il completamento delle istruzioni, ma il servizio di linguaggio deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia per definire un set di elementi di completamento candidato per l'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)