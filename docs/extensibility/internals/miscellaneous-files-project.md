---
title: Progetto file esterni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>Progetto file esterni
Quando un utente apre gli elementi di progetto, tutti gli elementi che non sono membri di tutti i progetti in una soluzione IDE assegna al progetto file esterni.  
  
 Progetti svolgono un ruolo significativo nel determinare quale editor viene utilizzato quando un utente apre un elemento di progetto. Un progetto può essere progettato per aprire determinati file utilizzando un editor specifico del progetto o un editor standard.  
  
 Un editor specifico del progetto in genere necessario che l'utente conoscenze specializzate o utilizzare le interfacce speciale dal progetto. Per ulteriori informazioni, vedere [procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor standard è possibile aprire qualsiasi file con un'estensione specifica in qualsiasi progetto. L'utente può personalizzare alcuni editor standard, ad esempio il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor di testo, per i progetti ma mantenere il carattere pubblico. Editor standard vengono create utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo.  
  
 Se nessun progetto nella soluzione risponde che è possibile aprire un elemento di progetto, l'IDE fornisce un particolare progetto denominato progetto di file esterni che consente di aprire qualsiasi file.  
  
 Questo progetto speciale fornisce per l'apertura di un file all'esterno del contesto di un progetto. Durante l'elaborazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> (metodo), il progetto file esterni risponde sempre con una priorità molto bassa. Di conseguenza, i vari file progetto sempre restituisce a qualsiasi progetto di priorità più alta che è possibile aprire i file.  
  
 Il progetto file esterni non richiede all'utente di creare in modo esplicito con il **nuovo progetto** la finestra di dialogo. Inoltre, il progetto file esterni non gestisce in modo permanente un elenco di membri del progetto. Usa una funzionalità facoltativa per registrare un elenco dei file utilizzati di recente per ogni utente.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Procedura: apertura degli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: apertura degli editor Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)