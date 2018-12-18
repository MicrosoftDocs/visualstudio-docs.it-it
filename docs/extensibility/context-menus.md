---
title: Menu di scelta rapida | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus"></a>Menu di scelta rapida
Menu di scelta rapida vengono visualizzati quando l'utente fa clic in un'area dell'area client attiva e cancellare quando viene rilasciato il pulsante destro del mouse.  
  
## <a name="editor-context-menus"></a>Editor - Menu di scelta rapida  
 Mediante l'intercettazione `ECMD_SHOWCONTEXTMENU`, il servizio di linguaggio è possibile controllare il menu di scelta rapida verrà visualizzato nell'editor. Per visualizzare il proprio menu di scelta rapida, gestiscono questo comando quando viene passato al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se non si gestisce questo comando, l'IDE visualizza un menu di scelta rapida standard fornito per l'editor. È inoltre possibile controllare il contenuto del menu di scelta rapida in una base per ogni marcatore. Per ulteriori informazioni, vedere [utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md) e [intercettazione di comandi del servizio di linguaggio Legacy](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio Legacy](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)