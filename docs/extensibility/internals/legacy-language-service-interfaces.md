---
title: Interfacce di servizio di linguaggio legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2861c4d6307442e1650b44d2b15f2a084ac7715
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-interfaces"></a>Interfacce di servizio di linguaggio legacy
Per un determinato linguaggio di programmazione, può essere solo un'istanza di un servizio di linguaggio alla volta. Tuttavia, un servizio di linguaggio singolo può essere utilizzato più di un editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non associare un servizio di linguaggio un editor specifico. Pertanto, quando si richiede un'operazione del servizio di linguaggio, è necessario identificare l'editor appropriato come parametro.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfacce comuni associate ai servizi di linguaggio  
 L'editor Ottiene il servizio di linguaggio chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> nel pacchetto VSPackage appropriato. Il servizio con ID (SID) passato nella chiamata di questo identifica il servizio di linguaggio richiesto.  
  
 È possibile implementare le interfacce del servizio del linguaggio core in un numero qualsiasi di classi separate. Tuttavia, un approccio comune consiste nell'implementare le interfacce seguenti in una singola classe:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facoltativo)  
  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia deve essere implementata in tutti i servizi di linguaggio. Fornisce informazioni sul servizio linguaggio, ad esempio il nome localizzato della lingua, le estensioni di file associate con il servizio di linguaggio e come recuperare una rappresentazione.  
  
## <a name="additional-language-service-interfaces"></a>Interfacce del servizio lingua aggiuntiva  
 Le altre interfacce possono essere forniti con il servizio di linguaggio. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede un'istanza separata di queste interfacce per ogni istanza del buffer del testo. Pertanto, è necessario implementare ognuna di queste interfacce nel proprio oggetto. Nella tabella seguente mostra le interfacce che richiedono un'istanza per ogni istanza di buffer di testo.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente di gestire aree di controllo finestra di codice, ad esempio la barra di menu a discesa. Questa interfaccia è possibile ottenere usando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo. È presente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per ogni finestra del codice.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Alla colorazione dei delimitatori e parole chiave del linguaggio. Questa interfaccia è possibile ottenere usando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> viene chiamato in fase di disegno. Evitare di lavoro a utilizzo intensivo di calcolo all'interno di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o le prestazioni potrebbero risultare compromesse.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce le descrizioni comandi parametro IntelliSense. Quando il servizio di linguaggio riconosce un carattere che indica che i dati (metodo) deve essere visualizzato, ad esempio una parentesi aperta, viene chiamato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo per notificare il testo visualizzare che il servizio di linguaggio in grado di visualizzare una descrizione comando informazioni di parametro. La visualizzazione del testo quindi richiama il servizio di linguaggio da utilizzano i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia da ottenere le informazioni necessarie per visualizzare la descrizione comandi.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornisce il completamento delle istruzioni IntelliSense. Quando il servizio di linguaggio è pronto per visualizzare un elenco di completamento, chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nella visualizzazione di testo. La visualizzazione del testo quindi richiama il servizio di linguaggio da utilizzando i metodi di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> oggetto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente la modifica della visualizzazione di testo utilizzando il gestore del comando. La classe in cui si implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaccia deve implementare anche il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Recupera la visualizzazione del testo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto eseguendo una query di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto passato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo). Dovrebbe esserci un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto per ogni visualizzazione.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercetta i comandi che l'utente digita nella finestra del codice. Monitorare l'output del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione per fornire informazioni sul completamento personalizzati e visualizzazione di modifica<br /><br /> Per passare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto per la visualizzazione del testo, chiamata <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)