---
title: 'Procedura: eseguire la registrazione per gli eventi nel Buffer di testo con l''API Legacy | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 94f2e781c316f3891fdef0c324d54fa2f9742222
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procedura: eseguire la registrazione per gli eventi nel Buffer di testo con l'API Legacy
Se il buffer di testo si accede tramite l'API legacy, è consigliabile registrare per gli eventi nel buffer di testo come illustrato nella procedura seguente.  
  
### <a name="to-advise-text-buffer-events"></a>Per indicare gli eventi nel buffer di testo  
  
1.  Da un puntatore a una delle interfacce in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chiamare `QueryInterface` per un puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> (metodo) e passare l'ID di interfaccia di eventi per il quale si desidera registrare.  
  
     Ad esempio, se si desidera registrare per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, quindi passare una ID di IID_IVsTextLinesEvents di interfaccia.  
  
     Il buffer di testo restituisce un puntatore al <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per l'oggetto punto di connessione appropriata.  
  
3.  Utilizzando l'indicatore di misura, chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> , passando un puntatore all'implementazione dell'interfaccia eventi per il quale si desidera registrare, ad esempio, il `IVsTextLinesEvents` interfaccia.  
  
     L'ambiente restituisce un cookie che è quindi possibile utilizzare per interrompere l'ascolto di eventi chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi nel Buffer di testo nell'API Legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)