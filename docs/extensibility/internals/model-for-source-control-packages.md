---
title: Modello per i pacchetti di controllo origine | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa0dcdd930412e4e53c59509848f0b7c1503c47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="model-for-source-control-packages"></a>Modello per i pacchetti di controllo di origine
Il modello seguente rappresenta un esempio di implementazione di un controllo di origine. Nel modello, vengono visualizzati le interfacce che è necessario implementare e i servizi di ambiente che è necessario chiamare. Ad esempio tutti i servizi, è effettivamente possibile chiamare i metodi di una determinata interfaccia che è possibile ottenere tramite il servizio. I nomi delle classi vengono identificati per rendere più semplice visualizzare l'esecuzione del controllo del codice sorgente.  
  
 ![Controllo del codice sorgente&#95;esempi TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Progetto di controllo di origine di esempio  
  
## <a name="interfaces"></a>Interfacce  
 È possibile implementare il codice sorgente per i nuovi tipi di progetto in Visual Studio usando l'elenco delle interfacce illustrato nella tabella seguente.  
  
|Interfaccia|Usa|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato da editor prima di non salvare o modifica (modificato) dei file e progetti. Questa interfaccia è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti per richiedere l'autorizzazione per aggiungere, rimuovere o rinominare un file o directory. Questa interfaccia viene anche chiamata da progetti per informare l'ambiente quando un componente approvati, rimuovere o rinominare l'azione è stata completata. È possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> servizio.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementata da qualsiasi entità che esegue la registrazione per ricevere una notifica quando i progetti di aggiungono, rinominano o rimuovere un file o directory. Per registrare la notifica dell'evento, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chiamato dai progetti per registrare con il pacchetto di controllo di origine e per ottenere informazioni sullo stato di controllo di origine. Questa interfaccia è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementato dal progetto di rispondere alle richieste di controllo di origine per informazioni sui file e per ottenere le impostazioni di controllo richiesto per il file di progetto di origine.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)