---
title: Supporto di automazione per le pagine di opzioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="automation-support-for-options-pages"></a>Supporto di automazione per le pagine di opzioni
VSPackage possono fornire personalizzato **opzioni** alle finestre di dialogo per la **strumenti** menu, pagine Opzioni del menu Strumenti, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e può renderli disponibili per il modello di automazione.  
  
## <a name="tools-options-pages"></a>Pagine Opzioni del menu Strumenti  
 Per creare un **opzioni del menu Strumenti** pagina, un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione di VSPackage il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo (o per codice gestito di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo).  
  
 È facoltativo, ma si consiglia di consentire l'accesso a questa nuova pagina tramite il modello di automazione. È possibile farlo tramite la procedura seguente:  
  
1.  Estendere la <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato da IDispatch.  
  
2.  Restituire un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo (o per il codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> (metodo)) per l'oggetto derivato da IDispatch.  
  
3.  Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo su un oggetto personalizzato **opzione** pagina delle proprietà, l'ambiente utilizza il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> per ottenere un oggetto personalizzato **opzioni del menu Strumenti** automazione della pagina implementazione.  
  
4.  L'oggetto di automazione di VSPackage viene quindi utilizzato per fornire a ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A>.  
  
 Per un esempio di implementazione di una pagina di opzioni del menu strumenti personalizzata, vedere [esempi di VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Vedere anche  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)