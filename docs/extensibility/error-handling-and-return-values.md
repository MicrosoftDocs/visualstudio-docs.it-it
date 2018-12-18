---
title: Gestione degli errori e i valori restituiti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1c9aa444860de2e20f51247ac53d16ceaad2b48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e i valori restituiti
I pacchetti VSPackage e COM utilizzano la stessa architettura per gli errori. Il `SetErrorInfo` e `GetErrorInfo` funzioni fanno parte delle Win32 application programming interface (API). Qualsiasi pacchetto VSPackage nell'ambiente di sviluppo integrato (IDE) può chiamare questi globale API Win32 per record informazioni complete sugli errori quando si riceve una notifica di errore. Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce gli assembly di interoperabilità per gestire le informazioni di errore.  
  
## <a name="interop-methods"></a>Metodi di interoperabilità  
 Per comodità, l'IDE fornisce un metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, utilizzare invece di chiamare le API Win32. Nel codice gestito, utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Quando un errore `HRESULT` raggiunge il livello in cui deve essere visualizzato il messaggio di errore (si tratta spesso dell'oggetto che implementa un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> gestore del comando), l'IDE Usa un altro metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, per visualizzare la finestra di messaggio appropriato. Nel codice gestito, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo.  
  
 Come un responsabile dell'implementazione di VSPackage, in genere implementano gli oggetti COM `ISupportErrorInfo`. Il `ISupportErrorInfo` interfaccia garantisce che informazioni dettagliate sull'errore è possibile spostare verticalmente fino alla catena di chiamata. Gli oggetti che potrebbero essere utilizzati tra processi o tra thread devono supportare `ISupportErrorInfo` per garantire che le informazioni dettagliate sull'errore correttamente sottoposto a marshalling al chiamante.  
  
 Tutti gli oggetti che sono correlate ai pacchetti VSPackage e che sono interessati a estendere l'IDE, tra cui factory editor, Editor, gerarchie e offerte di servizi, devono supportare informazioni dettagliate sull'errore. L'IDE non richiede tali oggetti VSPackage per implementare `ISupportErrorInfo`, sempre è sconsigliato.  
  
 L'IDE è responsabile per la segnalazione delle informazioni di errore e di visualizzarli all'utente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che un `HRESULT` viene propagata all'IDE. L'IDE è anche il meccanismo per la creazione di `ErrorInfo` oggetti.  
  
## <a name="general-guidelines"></a>Indicazioni generali  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodi per impostare e segnalare gli errori interni a anche l'implementazione di VSPackage. Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore nel pacchetto VSPackage:  
  
-   Implementare `ISupportErrorInfo` negli oggetti VSPackage COM.  
  
-   Creare un meccanismo che chiama di segnalazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo negli oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Consente di visualizzare gli errori agli utenti tramite l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo.  
  
## <a name="error-information-in-the-ide"></a>Informazioni sull'errore nell'IDE  
 Le regole seguenti indicano come gestire le informazioni di errore nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Come una strategia di difesa per garantire che info errore aggiornato non viene segnalato agli utenti, le funzioni che chiamano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo chiamare prima il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo. Passare `null` per cancellare i messaggi di errore memorizzato nella cache prima di chiamare qualsiasi elemento che è possibile impostare nuove informazioni sull'errore.  
  
-   Funzioni che sono direttamente i messaggi di errore sono consentite solo per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo se restituiscano un errore `HRESULT`. È possibile cancellare il `ErrorInfo` all'immissione di una funzione o la restituzione <xref:Microsoft.VisualStudio.VSConstants.S_OK>. L'unica eccezione a questa regola è quando una chiamata restituisce un errore `HRESULT` da cui possa ripristinare in modo esplicito o ignorare il ricevente.  
  
-   Qualsiasi entità che ha un errore viene ignorato in modo esplicito `HRESULT` deve chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. In caso contrario, il `ErrorInfo` oggetto può essere usato quando un'altra entità viene generato un errore senza fornire i propri accidentalmente `ErrorInfo`.  
  
-   Tutti i metodi che hanno origine errore `HRESULT` , si consiglia di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo per fornire informazioni dettagliate sull'errore. Se l'oggetto restituito `HRESULT` è una speciale `FACILITY_ITF` errori, quindi il metodo deve fornire una corretta `ErrorInfo`oggetto. Se l'errore restituito è un errore di sistema standard (ad esempio, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>e così via) è accettabile per restituire il codice di errore senza chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo. Come strategia di codifica difensiva, quando l'origine di un errore `HRESULT` (inclusi gli errori di sistema), chiamare sempre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (metodo), con `ErrorInfo` che descrive l'errore in modo più dettagliato, o `null`.  
  
-   Tutte le funzioni che restituiscono un errore generato da un'altra chiamata è necessario passare le informazioni che è stato ricevuto da ha generato l'errore chiamano nel `HRESULT` senza modificare il `ErrorInfo` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (componente automazione)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interfaccia ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)