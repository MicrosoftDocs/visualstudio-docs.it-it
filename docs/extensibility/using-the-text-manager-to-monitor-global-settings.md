---
title: Utilizzando la gestione di testo per monitorare le impostazioni globali | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 00716142e7f91d01fbc81c5d25b378065cb44f92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Utilizzando la gestione di testo per monitorare le impostazioni globali
Se si implementa un editor di componenti di base, è necessario monitorare le modifiche apportate alle impostazioni globali, perché queste modifiche potrebbero influenzare l'istanza dell'editor. È possibile rilevare le modifiche in attesa di eventi generati dal gestore del testo. Ad esempio, quando si specifica una preferenza globale per l'aspetto o il comportamento di un componente nell'editor di componenti di base, ad esempio un oggetto dati documento, il gestore di testo vengono archiviate queste informazioni e comunica a tutti i client interessati.  
  
## <a name="text-manager-functions"></a>Funzioni di gestione di testo  
 La gestione testi genera eventi per un numero di impostazioni, tra cui le operazioni seguenti:  
  
-   Se un buffer è nel controllo del codice sorgente  
  
-   Come registrare le notifiche di modifica di file  
  
-   Come tenere traccia delle visualizzazioni di cui sono associate a determinati buffer  
  
-   Preferenze di colorazione di testo  
  
-   Scheda e le preferenze di spazio  
  
 Le preferenze che sono univoche per una determinata lingua non sono gestite dal gestore del testo. Queste impostazioni devono essere gestite da ogni servizio di linguaggio.  
  
 Notifica degli eventi per la gestione di testo viene eseguito il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaccia. Implementare questa interfaccia nel client di oggetto per gestire gli eventi ha generato il gestore di testo. Registrare per questi eventi utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia del gestore di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Funzionalità dell'editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)