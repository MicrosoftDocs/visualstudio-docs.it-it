---
title: Oggetto VSTextView | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f169c3302b3e6fd72e5017193e34836ed3e5340e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vstextview-object"></a>Oggetto VSTextView
La visualizzazione del testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer del testo. In pratica, la visualizzazione è fare riferimento alla maggior parte degli utenti come l'editor. Poiché la vista è separata dal buffer tramite vari livelli di testo (ritorno a capo automatico, il testo della struttura e così via), la vista non deve necessariamente essere una rappresentazione esatta del testo nel buffer. Per ulteriori informazioni sulla visualizzazione di testo, vedere [accesso theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 La tabella seguente illustra le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte (vale a dire, azioni che vengono raggruppate in un'unità singola, annullare o ripristinare).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e la visualizzazione di accesso. `IVsTextView`non è thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con i livelli di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni per la vista da un thread diverso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)