---
title: Accesso ai Buffer di testo tramite l'API Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 77002e095690da85e73f1a79d405cb5174b96851
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Accesso ai Buffer di testo tramite l'API Legacy
Il testo è responsabile della gestione dei flussi di testo e salvataggio permanente di file. Anche se il buffer può leggere o scrivere altri formati, tutte le normali comunicazioni con il buffer viene eseguita utilizzando Unicode. Nelle API legacy, con il buffer di testo è possibile utilizzare uno - o un sistema di coordinate bidimensionale per identificare le posizioni di caratteri nel buffer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensioni di uno e due sistemi di Coordinate.  
 Posizione di una coordinata unidimensionale si basa sulla posizione del carattere dal primo carattere nel buffer, ad esempio 147. Utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaccia per accedere a una posizione nel buffer unidimensionale. Un sistema di coordinate bidimensionale si basa sulla coppia di riga e di indice. Ad esempio, un carattere nel buffer da 43 5 sarebbe su riga 43, cinque caratteri a destra del primo carattere in tale riga. Accedere a una posizione bidimensionale nel buffer tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia. Sia il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfacce vengono implementate dall'oggetto buffer di testo (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) e accessibile da altra utilizzando `QueryInterface`. Il diagramma seguente illustra queste e altre interfacce principali in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Oggetto TextBuffer](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Oggetto buffer di testo  
  
 Anche se uno dei sistemi di coordinate funziona nel buffer di testo, è ottimizzato per l'utilizzo di coordinate bidimensionali. Un sistema di coordinate unidimensionale è possibile creare un overhead delle prestazioni. Pertanto, utilizzare il sistema di coordinate bidimensionale laddove possibile.  
  
 Il testo responsabilità secondo del buffer è la persistenza di file. A tale scopo, l'oggetto di buffer di testo implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e opera come il componente di oggetto dati di documento per gli elementi di progetto e altri componenti dell'ambiente coinvolte nella persistenza. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [La modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Viene illustrato come modificare le impostazioni di visualizzazione utilizzando l'API legacy.  
  
 [Utilizzando la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato come utilizzare la gestione di testo per monitorare le impostazioni globali...  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)