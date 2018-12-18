---
title: Linee guida di controllo di origine aggiuntivi per i progetti e gli editor | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 308de182e604f06fff9ad25cb65428b2d48ff257
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida di controllo di origine aggiuntivi per i progetti e gli editor
Esistono alcune linee guida che progetti ed editor deve rispettare per supportare controllo del codice sorgente.  
  
## <a name="guidelines"></a>Indicazioni  
 Il progetto o un editor deve inoltre eseguire le operazioni seguenti per il supporto di controllo del codice sorgente:  
  
|Area|Progetto|Editor|Dettagli|  
|----------|-------------|------------|-------------|  
|Privato copie dei file|x||L'ambiente supporta private copie dei file. Ovvero, ogni persona elencata nel progetto ha proprio propria copia privata dei file in tale progetto.|  
|Persistenza ANSI o Unicode|x|x|Se si scrive il codice di persistenza, mantenere i file nel formato ANSI poiché la maggior parte dei programmi di controllo di origine non supportano Unicode.|  
|Enumerare i file|x||Il progetto deve contenere un elenco specifico di tutti i file all'interno di esso e deve essere in grado di enumerare l'elenco di file utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve esporre anche i nomi di elemento con il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementazione e supporto di ricerca del nome (inclusi i file speciali) tramite il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementazione.|  
|Formato di testo|x|x|Se possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. Impossibile unire file che non sono in formato testo con altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|  
|Basato sul riferimento|x||Progetti basato sul riferimento facilmente sono supportati nel controllo del codice sorgente. Tuttavia, progetti basati su directory supportati anche dal controllo del codice sorgente, purché il progetto può produrre un elenco dei file su richiesta, indipendentemente dall'esistano di tali file sul disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto diventa inattivo prima di qualsiasi file.|  
|Rendere persistenti di oggetti e proprietà in ordine prestabilito|x|x|Mantenere i file in un ordine prestabilito, ad esempio ordine alfabetico, per facilitare l'unione.|  
|Ricarica|x|x|Quando viene modificato un file su disco, l'editor deve essere in grado di ricaricare il file. Quando partecipa a controllo del codice sorgente, l'ambiente ricarica dati per l'utente chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. La più difficile Ricarica si verifica quando si verifica un checkpoint quando è stato chiamato IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e l'elaborazione di informazioni. Tuttavia, il codice di ricaricamento deve essere in grado di eseguire in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, è necessario implementare un progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> se è nidificata gerarchie per supportare il ricaricamento annidati di file di progetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)