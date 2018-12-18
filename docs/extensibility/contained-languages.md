---
title: Lingue di contenuti | Documenti Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf2c63a66ba76b65d1caec2c5eed006d57fca0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="contained-languages"></a>Lingue indipendente

*Contenuti lingue* linguaggi sono contenuti in altri linguaggi. Ad esempio HTML in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] potrebbero contenere pagine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] script. Un'architettura dual-language è necessaria per l'editor di file con estensione aspx fornire IntelliSense, colorazione e altre funzionalità di modifica per il codice HTML e il linguaggio di scripting.

## <a name="implementation"></a>Implementazione

L'interfaccia più importante, è necessario implementare per lingue indipendente è la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato all'interno di una lingua principale. Fornisce l'accesso per il servizio di linguaggio rappresentazione, il filtro di visualizzazione di testo e ID lingua principale del servizio. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> consente di creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. La procedura seguente viene illustrato come implementare un linguaggio indipendente:

1.  Utilizzare `QueryService()` language ID servizio e l'ID di interfaccia di ottenere il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Per creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> l'interfaccia, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodo. Passare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia, una o più [elemento ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia.

3.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia, ovvero l'oggetto TextBuffer coordinator, fornisce i servizi di base necessarie per eseguire il mapping di indirizzi in un file primario nel buffer del linguaggio secondario.

     Ad esempio, in un unico file aspx, il file primario include ASP, HTML e tutto il codice che è contenuto. Tuttavia, il buffer secondario include solo il codice contenuto insieme a tutte le definizioni di classe, per rendere il buffer secondario di un file di codice valido. Il coordinatore buffer gestisce le operazioni di coordinare le modifiche da un buffer per l'altro.

4.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> metodo, che è la lingua principale, indica il coordinatore di buffer viene eseguito il mapping di testo all'interno del buffer di testo corrispondente nel buffer secondario.

     Il linguaggio passa una matrice del <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struttura, che attualmente include solo un database primario e un intervallo secondario.

5.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> (metodo) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metodo fornisce il mapping da primario a un buffer secondario e viceversa.