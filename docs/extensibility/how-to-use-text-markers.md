---
title: 'Procedura: utilizzare gli indicatori di testo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>Procedura: utilizzare gli indicatori di testo
Marcatori di testo possono essere applicati per modificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-apply-text-markers"></a>Per applicare i marcatori di testo  
  
1.  Ottiene un'istanza di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    >  L'editor di componenti di base applica automaticamente i marcatori di testo standard a qualsiasi documento che sta modificando e non può essere necessario applicare in modo esplicito i marcatori di testo standard.  
  
2.  Ottenere un ID di tipo marcatore dell'indicatore di cui si è interessati chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodo con il `GUID` dell'indicatore di testo che si desidera utilizzare.  
  
    > [!NOTE]
    >  Non utilizzare il `GUID` del pacchetto VSPackage o del servizio che fornisce l'indicatore di testo.  
  
3.  Utilizzare l'ID del tipo di marcatore ottenuto chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> un parametro di chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> (metodo) o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> per applicare un indicatore di testo per una determinata area di testo.  
  
#### <a name="to-add-features-to-text-markers"></a>Per aggiungere funzionalità a marcatori di testo  
  
1.  Potrebbe essere opportuno aggiungere ulteriori funzionalità a un indicatore di testo, ad esempio descrizioni comandi, menu di scelta rapida speciale o gestore circostanze speciali. A tale scopo:  
  
2.  Creare un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
3.  Se si desidera usare funzionalità aggiuntive, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfacce sullo stesso oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia.  
  
4.  Passare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia creati dall'utente, la chiamata al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodo o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodo utilizzato per applicare l'indicatore di testo a un'area di testo specificata.  
  
5.  Durante l'aggiunta di supporto tecnico dal menu di contesto a un'area indicatore di testo è necessario creare i menu.  
  
     Per ulteriori informazioni su come creare un contesto menu, vedere [menu di scelta rapida](../extensibility/context-menus.md).  
  
6.  Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente chiama i metodi delle interfacce fornite, ad esempio il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metodo, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodo in base alle esigenze.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)