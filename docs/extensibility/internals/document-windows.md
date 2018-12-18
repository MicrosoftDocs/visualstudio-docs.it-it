---
title: Finestre dei documenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio, un *finestra del documento* è una finestra cornice figlio che è associata a una finestra di interfaccia a documenti multipli (MDI). Le finestre dei documenti vengono generalmente utilizzate per la visualizzazione e modifica di codice sorgente o di testo, ma può ospitare anche altri tipi di funzionalità. Finestre di documento:  
  
-   Possono essere organizzati in gruppi di scheda separata orizzontale o verticale del padre MDI in modo che sia possono visualizzare più file contemporaneamente.  
  
-   Possono essere ancorate in qualsiasi ordine del padre MDI.  
  
-   Può essere mobile liberamente.  
  
-   Sono collegate in ordine di tabulazione ad altre finestre MDI.  
  
 I comandi per il raggruppamento, ancorate e mobili sono disponibili nel menu di scelta rapida per una scheda della finestra documento.  
  
 Per ulteriori informazioni sul comportamento delle finestre in Visual Studio, vedere [personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementazione di finestra di documento  
 Le finestre dei documenti vengono create implementando un editor. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia crea le finestre dei documenti come parte di un'istanza di un editor. Per ulteriori informazioni, vedere [interfacce Legacy nell'Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Per fornire all'indietro e inoltrare i punti di navigazione in una finestra, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaccia. L'editor di testo utilizza dei marcatori di testo per identificare i punti di navigazione nel documento.  
  
## <a name="the-running-document-table"></a>Tabella Document in esecuzione  
 L'IDE Usa la tabella documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. Il RDT è il meccanismo tramite il documento di windows viene inviata una notifica degli eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per ulteriori informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento dei documenti ritardato](../../extensibility/internals/delayed-document-loading.md)