---
title: Oggetto VSCodeWindow | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2b1d85eea974e67ae37f8d4d5bfd7aa0069e92b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
Una finestra del codice è una finestra del documento specializzato che può includere uno o più visualizzazioni di testo, in genere il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 L'architettura della finestra del codice è una finestra del documento che si trova all'interno di una cornice di finestra. A livello funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. In modalità interfaccia a documenti multipli (MDI), la finestra del codice è il frame MDI figlio. Per ulteriori informazioni, vedere [la personalizzazione di codice Windows tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Nella tabella seguente sono incluse le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generici per individuare un servizio che identifica un identificatore univoco globale (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI (interfaccia) di documento più contenente una o più visualizzazioni di codice.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice di finestra.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)