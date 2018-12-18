---
title: Personalizzazione di codice Windows tramite l'API Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f0b00c31280b9471da99aea55118e25dd551ad96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalizzazione di codice Windows tramite l'API Legacy
Una finestra del codice è un oggetto finestra di documento che supporta uno o più visualizzazioni di testo. Esattamente le stesse funzionalità di una finestra del codice dipendono dal servizio di linguaggio associato. In modalità interfaccia a documenti multipli (MDI), la finestra del codice è il frame MDI figlio.  
  
 Finestre del codice sono controllati da servizi di linguaggio e ogni servizio di linguaggio possa fornire il proprio gestore di finestra di codice. In questo modo il servizio di linguaggio aggiungere le proprie aree di controllo alla finestra del codice, ad esempio linee a zigzag, colorazione e altro ancora. Per ulteriori informazioni su come creare una finestra principale, vedere [creazione di componenti di base dell'Editor mediante l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una finestra del codice è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto con una visualizzazione di testo e le aree di controllo posizionati nell'oggetto. Quando si crea la finestra del codice durante la creazione di istanze di base dell'editor, il servizio di linguaggio è possibile collegare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> alla finestra del codice, come è illustrato nella figura seguente.  
  
 ![Immagine di CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Finestra del codice  
  
 Il servizio di linguaggio implementa la gestione di finestre del codice ed è responsabile per la gestione di aree di controllo, ad esempio una barra di menu a discesa. Il finestra di codice chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo durante l'inizializzazione di finestra di codice. Quando viene effettuata la chiamata, il servizio di linguaggio è possibile aggiungere una barra dei menu a discesa o una barra dei pulsanti (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) alla finestra del codice.  
  
## <a name="in-this-section"></a>In questa sezione  
 `Customizing Code Windows by Using the Legacy API`  
 Viene descritto come personalizzare finestre del codice tramite l'API legacy.  
  
 [Procedura: ospitare un Editor in un altro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Viene illustrato come ospitare un secondo revisore all'interno di una finestra dell'editor.  
  
 [Procedura: generare eventi quando l'Editor perde lo stato attivo](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Viene illustrato come associare una visualizzazione del documento a un oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Creazione di istanze di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)