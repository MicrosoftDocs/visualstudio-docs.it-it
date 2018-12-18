---
title: I filtri di servizio importanti comandi per la lingua | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee6c746874e7e00643f1b840185969a6dabadfe5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri di servizio di linguaggio
Se si desidera creare un filtro di servizio di linguaggio completo, prendere in considerazione i seguenti comandi di gestione. L'elenco completo degli identificatori di comando è definito nel <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione per codice gestito e l'intestazione Stdidcmd.h file per non gestita [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] codice. È possibile trovare il file Stdidcmd.h *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Comandi da gestire  
  
> [!NOTE]
>  Non è obbligatoria per filtrare per tutti i comandi nella tabella seguente.  
  
|Comando|Descrizione|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic. Questo comando indica che è necessario fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza i comandi specifici della lingua. Per includere i comandi in questo menu, gestire il comando e visualizzare un menu di scelta rapida manualmente.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + J. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per visualizzare la finestra di completamento istruzione.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita un carattere. Monitorare questo comando per determinare quando viene digitato un carattere di trigger e per fornire l'istruzione completamento, suggerimenti di metodo e i marcatori di testo, ad esempio la colorazione della sintassi, corrispondenza tra parentesi graffe e marcatori di errore. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per il completamento delle istruzioni e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> per suggerimenti di metodo. Per supportare i marcatori di testo, monitorare questo comando per determinare se il carattere digitato è necessario aggiornare gli indicatori.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto INVIO. Monitorare questo comando per determinare il momento chiudere una finestra del suggerimento metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Per impostazione predefinita, la visualizzazione del testo gestisce questo comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto Backspace. Monitoraggio per determinare quando chiudere una finestra del suggerimento metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Per impostazione predefinita, la visualizzazione del testo gestisce questo comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o un tasto di scelta rapida. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiornare la finestra di comando con le informazioni sui parametri.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente viene posizionato su una variabile o posiziona il cursore su una variabile e seleziona **informazioni rapide** da **IntelliSense** nel **modifica** menu. Restituire il tipo della variabile in un suggerimento chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Se il debug è attivo, il suggerimento deve inoltre in grado di visualizzare il valore della variabile.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + BARRA SPAZIATRICE. Questo comando indica al servizio di linguaggio per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere **Commenta selezione** o **rimuovere il commento selezione** da **avanzate** nel **modifica** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica che l'utente desidera impostare come commento il testo selezionato. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera rimuovere il commento al testo selezionato. Questi comandi possono essere implementati solo dal servizio di linguaggio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)