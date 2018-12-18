---
title: Gestione di annullamento e ripetizione tramite l'API Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c50316b7d5786b1fb3f07255eaf4d875f7f41e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Annullamento di gestione e il ripristino tramite l'API Legacy
Editor devono supportare le operazioni di annullamento che consentono agli utenti di annullare le modifiche apportate di recente quando si modifica codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.  
  
 [Procedura: cancellare lo Stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare un stack di annullamento.  
  
 [Procedura: utilizzare Gestione fase di rollback collegata](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora gestione fase di rollback collegata nell'editor.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione di rollback per un editor che supporta più viste.  
  
## <a name="related-sections"></a>Sezioni correlate