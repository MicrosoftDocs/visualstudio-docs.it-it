---
title: 'Procedura: aggiornare la barra di stato | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b5f7e6849736f0fc226c51f69a1526aca8e971a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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