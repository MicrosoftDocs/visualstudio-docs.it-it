---
title: L'accesso a livelli di testo tramite l'API Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d21b31940f1e1ebca767b9d3f0cf5ab802181bda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>L'accesso ai livelli di testo tramite l'API Legacy
In genere, un livello testo incapsula alcuni aspetti di layout del testo. Ad esempio, un livello "una funzione-tempo" nascosta testo prima e dopo una funzione che contiene il punto di inserimento (il punto di inserimento di testo).  
  
 Un livello di testo si trova tra un buffer e una visualizzazione e modifica il modo in cui che la vista visualizza i contenuti del buffer.  
  
## <a name="text-layer-information"></a>Informazioni sul livello di testo  
 Nell'elenco seguente viene descritto il funzionano di livelli di testo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Il testo in un livello di testo può decorare con marcatori e la colorazione della sintassi.  
  
-   Attualmente non è possibile implementare il propria livelli.  
  
-   Espone un livello <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, che deriva da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Lo stesso buffer di testo viene inoltre implementato come livello, che consente una visualizzazione gestire in modo polimorfico livelli sottostanti.  
  
-   Un numero qualsiasi di livelli può essere compresa tra la visualizzazione e il buffer. Ogni livello riguarda solo il livello sottostante e la visualizzazione si occupa principalmente di livello superiore. (La vista dispone di alcune informazioni sul buffer.)  
  
-   Un livello può influire sulle solo i livelli sottostanti. E non influisce sui livelli sopra di esso oltre l'origine eventi standard.  
  
-   Nell'editor di testo nascosto, il testo sintetico e ritorno a capo automatico vengono implementati come livelli. È possibile implementare il testo nascosto e sintetico senza interagire direttamente con i livelli. Per ulteriori informazioni, vedere [struttura in un servizio di linguaggio Legacy](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Ogni livello di testo ha un proprio sistema di coordinate locale che viene esposta tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfaccia. Il livello di riga a capo automatico, ad esempio, potrebbe contenere due righe mentre il buffer di testo sottostante può contenere solo una riga.  
  
-   La vista comunica ai livelli tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfaccia. Utilizzare questa interfaccia per risolvere le differenze tra le coordinate di visualizzazione con le coordinate di buffer.  
  
-   Uno dei livelli, ad esempio il livello di testo sintetici che ha origine il testo deve fornire un'implementazione locale di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Oltre a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, deve implementare un livello testo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e generare gli eventi nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Sintassi colorazione nell'editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizzazione di menu e controlli di Editor utilizzando l'API Legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)