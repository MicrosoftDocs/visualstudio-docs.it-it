---
title: 'Procedura: aggiungere testo Standard marcatori | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bdcdbabae26a9116b1e00910ecef2f83f4075551
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-standard-text-markers"></a>Procedura: aggiungere testo Standard marcatori
Utilizzare la procedura seguente per creare uno dei tipi di marcatori di testo predefinito forniti con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale.  
  
### <a name="to-create-a-text-marker"></a>Per creare un indicatore di testo  
  
1.  A seconda se si utilizza uno o due - dimensionale di sistema di coordinate, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo per creare un nuovo indicatore di testo.  
  
     In questa chiamata al metodo, specificare un tipo di marcatore, un intervallo di testo per creare il marcatore e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia. Quindi, questo metodo restituisce un puntatore al marcatore di testo appena creato. Tipi di marcatori vengono prelevati i <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumerazione. Specificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia se si desidera essere informati degli eventi di marcatore.  
  
    > [!NOTE]
    >  Creare marcatori di testo nel thread principale della UI solo. L'editor di componenti di base si basa sul contenuto del buffer di testo per creare gli indicatori di testo e il buffer di testo non è thread-safe.  
  
## <a name="adding-a-custom-command"></a>Aggiunta di un comando personalizzato  
 Implementazione di `IVsTextMarkerClient` interfaccia e fornisce un puntatore a esso da un marcatore migliora il comportamento di marcatore in diversi modi. In primo luogo, consente di fornire suggerimenti per un segno di spunta e per eseguire i comandi. Questo consente inoltre di ricevere le notifiche degli eventi per i singoli marcatori e per creare un menu di scelta rapida personalizzato sul marcatore. Utilizzare la procedura seguente per aggiungere un comando personalizzato per il menu di scelta rapida marcatore.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Per aggiungere un comando personalizzato a menu di scelta rapida  
  
1.  Prima che venga visualizzato il menu di scelta rapida, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metodo e passa il puntatore al marcatore di testo è interessato e il numero dell'elemento di comando nel menu di scelta rapida.  
  
     Ad esempio, i comandi specifici del punto di interruzione nel menu di scelta rapida includono **Rimuovi punto di interruzione** tramite **nuovo punto di interruzione**, come visualizzato nella schermata seguente.  
  
     ![Menu di scelta rapida marcatore](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Passare nuovamente un testo che identifica il nome del comando personalizzato. Ad esempio, **Rimuovi punto di interruzione** potrebbe essere un comando personalizzato se l'ambiente non ha già fornito. Anche passare nuovamente se il comando è supportato, disponibile e abilitato, e/o un elemento toggle di attivazione / disattivazione. L'ambiente utilizza queste informazioni per visualizzare il comando personalizzato nel menu di scelta rapida in modo corretto.  
  
3.  Per eseguire il comando, l'ambiente chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> , passando è un puntatore per l'indicatore di testo e il numero del comando scelto dal menu di scelta rapida.  
  
     Utilizzare queste informazioni da questa chiamata per eseguire tutte le azioni dell'indicatore di testo del comando personalizzato impone.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: creare marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)