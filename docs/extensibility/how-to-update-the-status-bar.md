---
title: 'Procedura: aggiornare la barra di stato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>Procedura: aggiornare la barra di stato
Il **barra di stato** una barra di controllo si trova nella parte inferiore di molte finestre dell'applicazione che contiene uno o più righe di testo di stato o gli indicatori.  
  
### <a name="to-update-the-status-bar"></a>Per aggiornare la barra di stato  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> su ogni oggetto di visualizzazione (DocView) che fornisce un editor, ad esempio una visualizzazione form e una visualizzazione di codice.  
  
2.  Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aggiornare le informazioni contenute nel **barra di stato** chiamando i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo quando la finestra del documento viene inizialmente attivata. Per il resto del tempo che la finestra di documento è attiva, è necessario aggiornare il **barra di stato** informazioni come lo stato delle modifiche dell'editor.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Oggetto **barra di stato** contiene quattro campi distinti:  
  
-   Testo di stato  
  
-   Indicatore di stato  
  
-   Icona animata  
  
-   Informazioni sull'editor  
  
 Per ulteriori informazioni, vedere [barre di stato](/cpp/mfc/status-bars).  
  
 Chiama automaticamente l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementazione quando viene attivata la finestra del documento.  
  
 Il responsabile dell'implementazione di VSPackage è responsabile per l'aggiornamento del testo di stato nella barra di stato. L'IDE Reimposta la stringa di "Pronto" se il campo di testo di stato è impostato su text vuota ("") nel tempo di inattività.  
  
## <a name="see-also"></a>Vedere anche  
 [Barre di stato](/cpp/mfc/status-bars)