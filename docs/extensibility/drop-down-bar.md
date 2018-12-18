---
title: Barra dei menu a discesa | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cf01e8a416407c570076812bf18aa6b21c21583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="drop-down-bar"></a>Barra dei menu a discesa
Barra dei menu a discesa viene fornita nella parte superiore della finestra del codice e contiene due elenchi a discesa.  
  
## <a name="drop-down-bar-interfaces"></a>Barra dei menu a discesa interfacce  
 In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], ad esempio, la barra dei menu a discesa contiene gli elenchi per [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementi e [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le funzioni membro di elementi, come illustrato nell'immagine seguente.  
  
 ![Eliminare&#45;verso il basso le barre](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barra dei menu a discesa  
  
 Quando si implementa una barra dei menu a discesa, sono disponibili quattro interfacce di primaria importanza:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementare questa interfaccia per l'inserimento del contenuto della barra dei menu a discesa. Ogni combinazione di riepilogo a discesa può contenere testo normale o testo artistico (grassetto, sottolineato o corsivo), può avere colorazione del tipo di carattere testo finestra o tipo di carattere grigio colorazione e facoltativamente, è possibile specificare una bitmap piccola accanto alla voce dell'elenco a discesa. Simile al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia, le immagini bitmap fornite negli elenchi di immagini. Ogni combinazione di riepilogo a discesa può avere un elenco di immagini differenti; Tuttavia, ciascun elenco immagini deve contenere le immagini della stessa altezza. Inoltre, l'uso di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> (metodo), è possibile fornire una descrizione comando per ogni combinazione.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chiamare questa interfaccia per creare o eliminare la barra di menu a discesa per una finestra del codice. Questa interfaccia può essere utilizzata anche per determinare se una barra dei menu a discesa è già connesso a una finestra del codice tramite la chiamata di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metodo. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Chiamare questa interfaccia per comunicare direttamente con la barra dei menu a discesa. È possibile utilizzare questa interfaccia per forzare un aggiornamento dell'elenco a discesa della barra di contenuto o per modificare la selezione in una delle caselle di riepilogo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se è stato registrato il `ShowDropdownBarOption` chiave del Registro di sistema del servizio del linguaggio, quindi la gestione di finestre di codice necessario monitorare questo evento per la sincronizzazione con le preferenze dell'utente relative se deve essere visualizzata la barra di elenco a discesa. Se questa opzione non registrare chiave del linguaggio del servizio, quindi l'opzione per mostrare o nascondere la barra dei menu a discesa è disabilitata nel **opzioni** menu.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Collegamento di una barra dei menu a discesa a una finestra del codice  
 Per collegare una barra dei menu a discesa nella finestra di codice quando viene creato, un servizio di linguaggio deve connettersi per l'elenco a discesa barra quando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo viene chiamato. Se una chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metodo indica che una barra dei menu a discesa non esista già, quindi chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Per l'accesso di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfaccia, chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntatore restituito all'utente quando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementazione è stata collegata.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di codice Windows tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)