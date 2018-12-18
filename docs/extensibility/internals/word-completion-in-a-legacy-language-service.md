---
title: Completamento di Word in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a4ab4bd29c753fc03787fbbadbe106d2d8862b10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>Completamento delle parole in un servizio di linguaggio Legacy
I caratteri mancanti su una parola parziale digitata viene compilato il completamento delle parole. Se è presente un solo termine possibili, la parola viene completata quando si immette il carattere di completamento. Se la parola parziale corrisponde a più possibilità, viene visualizzato un elenco di possibili completamenti. Un carattere di completamento può essere qualsiasi carattere che non viene utilizzato per gli identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [estensione dell'Editor e i servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation-steps"></a>Passaggi di implementazione  
  
1.  Quando l'utente seleziona **completa parola** dal **IntelliSense** dal menu di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando viene inviato al servizio di linguaggio.  
  
2.  Il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta le chiamate di <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (metodo) con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  Il <xref:Microsoft.VisualStudio.Package.Source> la classe e infine chiama la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo per ottenere l'elenco dei completamenti word possibili e visualizza quindi le parole in una descrizione comando elenco utilizzando il <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     Se è presente una sola parola corrispondente, la <xref:Microsoft.VisualStudio.Package.Source> classe completa parola.  
  
 In alternativa, se lo scanner restituisce il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando viene inserito il primo carattere di un identificatore, il <xref:Microsoft.VisualStudio.Package.Source> classe lo rileva e chiama il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (metodo) con il motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>. In questo caso, il parser deve rilevare la presenza di un carattere di selezione membro e fornire un elenco di membri.  
  
## <a name="enabling-support-for-the-complete-word"></a>Abilitazione del supporto per la parola completa  
 Per abilitare il supporto per set di completamento di word la `CodeSense` passato al parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Il parser deve restituire un elenco di dichiarazioni in risposta al valore di motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>, per il completamento delle parole a funzionare.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementazione completa parola nel metodo ParseSource  
 Per il completamento delle parole, il <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe per ottenere un elenco di corrispondenze possibili word. È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere la <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi è necessario implementare.  
  
 Se l'elenco contiene solo una singola parola, la <xref:Microsoft.VisualStudio.Package.Source> classe inserisce automaticamente tale parola al posto di parole parziali. Se l'elenco contiene più di una parola, la <xref:Microsoft.VisualStudio.Package.Source> classe visualizza un elenco di comandi dello strumento da cui l'utente può selezionare l'opzione desiderata.  
  
 Esaminare inoltre l'esempio di un <xref:Microsoft.VisualStudio.Package.Declarations> implementazione della classe in [membro completamento in un servizio di linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).