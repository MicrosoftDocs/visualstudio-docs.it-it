---
title: Lingue di contenuti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bfdbc3d1c0e7bbc0b3dc712d9434ca1b49c6feca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contained-languages"></a>Lingue indipendente
*Contenuto lingue* sono le lingue incluse in altri linguaggi. Ad esempio HTML in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] potrebbero contenere pagine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] script. Un'architettura dual-language è necessaria per l'editor di file con estensione aspx fornire IntelliSense, colorazione e altre funzionalità di modifica per il codice HTML e il linguaggio di scripting.  
  
## <a name="implementation"></a>Implementazione  
 L'interfaccia più importante, è necessario implementare per lingue indipendente è la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Questa interfaccia viene implementata da qualsiasi linguaggio che può essere ospitato all'interno di una lingua principale. Fornisce l'accesso per il servizio di linguaggio rappresentazione, il filtro di visualizzazione di testo e ID lingua principale del servizio. Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> consente di creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. La procedura seguente viene illustrato come implementare un linguaggio indipendente:  
  
1.  Utilizzare `QueryService()` language ID servizio e l'ID di interfaccia di ottenere il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodo per creare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaccia. Passare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia, un ID di elemento (una o più delle <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, o <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia.  
  
3.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaccia, ovvero l'oggetto TextBuffer coordinator, fornisce i servizi di base necessarie per eseguire il mapping di indirizzi in un file primario nel buffer del linguaggio secondario.  
  
     Ad esempio, in un unico file aspx, il file primario include ASP, HTML e tutto il codice contenuto. Tuttavia, il buffer secondario, include solo il codice contenuto insieme a tutte le definizioni di classe, per rendere il buffer secondario di un file di codice valido. Il coordinatore buffer gestisce le operazioni di coordinare le modifiche da un buffer per l'altro.  
  
4.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> metodo, che è la lingua principale, indica il coordinatore di buffer viene eseguito il mapping di testo all'interno del buffer di testo corrispondente nel buffer secondario.  
  
     Il linguaggio passa una matrice del <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struttura, che attualmente include solo un database primario e un intervallo secondario.  
  
5.  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> (metodo) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metodo fornisce il mapping da primario a un buffer secondario e viceversa.