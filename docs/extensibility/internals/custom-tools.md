---
title: Gli strumenti personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7589c9a2aedf987af79689e8babccb554fbb4ccc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti personalizzati* consentono di associare uno strumento con un elemento in un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Alcuni strumenti personalizzati, dette *generatori di file singolo*, vengono spesso utilizzati per implementare funzioni di conversione che genera il codice dai dati e viceversa. Ad esempio, di creare generatori di file singolo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] codice non i file resx e. Settings dell'origine. Il codice sorgente generato fornisce accesso fortemente tipizzato ai dati nei file resx e. Settings. Il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto supportano strumenti personalizzati. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] non tipi di progetto. I tipi di progetto possono supportare anche gli strumenti personalizzati.  
  
 Gli strumenti personalizzati sono registrati i componenti che implementano il `IVsSingleFileGenerator` interfaccia.  
  
 Gli strumenti personalizzati sono associati un `ProjectItem` oggetto di interfaccia e sono simili a editor e finestre di progettazione. Uno strumento personalizzato accetta il file rappresentato da un `ProjectItem` come input e scrive un nuovo file il cui nome viene fornito per il `DefaultExtension` metodo.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)  
 Viene descritto come utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia da implementare uno strumento personalizzato.  
  
 [Registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)  
 Fornisce le descrizioni di tutte le voci del Registro di sistema per uno strumento personalizzato.  
  
 [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Viene illustrato come sistemi di progetto forniscono il supporto per finestre di progettazione visiva per tipi e le classi di accesso generato tramite il file eseguibile portabile (PE) temporaneo.  
  
 [Salvataggio permanente della proprietà di un elemento di progetto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Viene illustrato come mantenere una proprietà dell'elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Vengono fornite informazioni dettagliate sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, che consente di trasformare un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.  
  
 <xref:EnvDTE.ProjectItem>  
 Viene illustrato il `ProjectItem` interfaccia che rappresenta un elemento in un progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Vengono fornite informazioni dettagliate sul `DefaultExtension` metodo, che recupera l'estensione di file che viene assegnato il nome del file di output.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estensione dei progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti e soluzioni per organizzare i file di codice e file di risorse e come implementare il codice sorgente.