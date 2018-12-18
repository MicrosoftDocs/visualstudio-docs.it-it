---
title: L'accesso a theText visualizzazione tramite l'API Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>L'accesso a theText visualizzazione tramite l'API Legacy
Una visualizzazione di testo è una presentazione del testo che viene archiviato in un buffer di testo. La visualizzazione del testo è possibile accedere tramite l'API legacy, come illustrato nella sezione seguente.  
  
## <a name="text-view-object"></a>Oggetto TextView  
 Ogni visualizzazione è associato un proprio buffer di testo e la vista è una finestra sui dati nel buffer. Il diagramma seguente mostra le interfacce dell'oggetto visualizzazione testo, rappresentato dalla chiave <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Visualizzazione oggetto testo di Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Oggetto TextView  
  
 La vista è un modo per presentare il testo nel buffer. Sono disponibili funzionalità quali ritorno a capo automatico e la struttura, in modo che sia visualizzata nella vista non è una rappresentazione esatta del testo nel buffer.  
  
 Una vista consente di altri servizi o processi per l'intercettazione di comandi in ingresso e agire di conseguenza, prima della visualizzazione interviene su di essi. Il servizio per eseguire questa operazione più comune è un servizio di linguaggio. Un servizio di linguaggio potrebbe essere necessario, ad esempio, di intercettare il comando per il tasto INVIO fornire suggerimenti di comportamento o lo strumento rientri personalizzati.  
  
## <a name="adding-functionality-to-the-text-view"></a>Aggiunta di funzionalità per la visualizzazione del testo  
 È possibile personalizzare il comportamento di visualizzazione testo gestendo specifiche combinazioni di tasti. Per intercettare le sequenze di tasti, implementano <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sull'oggetto e fornire una destinazione di comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) per i comandi di monitoraggio e l'intersezione.  
  
 Visualizzazione di testo utilizza sequenza architettura per i filtri dei comandi. Nuovi filtri dei comandi (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetti) vengono aggiunte alla sequenza chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo.  
  
 Notifica degli eventi per la visualizzazione del testo è disponibile utilizzando la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaccia. Implementare questa interfaccia per l'oggetto client per ricevere la notifica delle modifiche per la visualizzazione del testo. Esporre l'interfaccia per la visualizzazione del testo utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella visualizzazione di testo per ricevere una notifica di modifiche dalla vista.  
  
## <a name="see-also"></a>Vedere anche  
 [La modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Utilizzando la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)