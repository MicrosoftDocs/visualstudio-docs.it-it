---
title: 'Procedura: ospitare un Editor in un altro Editor | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 685ad1d619fdf9f04fe1a9cd1122a9e6ed3ba025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Procedura: ospitare un Editor in un altro Editor
In Visual Studio è possibile ospitare un editor all'interno di un altro, specificando la finestra di hosting come finestra padre. A tale scopo, impostare i parametri <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> nella cornice della finestra figlio.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Per impostare la cornice della finestra per ospitare un editor  
  
1.  Designare un editor come editor ospitato tramite la creazione di un riquadro della finestra figlio.  
  
     In questo riquadro è cui passa il testo dell'editor.  
  
2.  Creare l'editor di hosting usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metodo.  
  
3.  Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> proprietà nell'implementazione di cornice della finestra dell'editor ospitato passando queste proprietà come parametri per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (metodo), rispettivamente.  
  
     Se è necessario recuperare questi parametri, passare a queste proprietà per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo.  
  
4.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per l'editor di contenuto.  
  
     Nel riquadro dell'editor contenente ospitato verrà visualizzato l'editor.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il **Application Designer** in Visual Studio Team Edition for Architects è riportato un esempio di una cornice della finestra dell'editor hosting di un altro editor. Il **Application Designer** ospita altre finestre di progettazione nel relativo riquadro di destra. Un pannello della finestra di progettazione (o **proprietà** pagina) per ognuna delle finestre di progettazione contenute viene aggiunto per la cornice della finestra contenitore.