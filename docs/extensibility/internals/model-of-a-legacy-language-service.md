---
title: Modello di un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 943f0f013045e3082af3069ed4d45aaed1096869
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio Legacy
Un servizio di linguaggio definisce gli elementi e le funzionalità per una lingua specifica e viene utilizzato per fornire l'editor con informazioni specifiche per tale lingua. Ad esempio, l'editor deve conoscere le parole chiave del linguaggio e elementi per supportare la colorazione della sintassi.  
  
 Il servizio di linguaggio collabora a stretto contatto con il buffer di testo mediante l'editor e la vista che contiene l'editor. Microsoft IntelliSense **informazioni rapide** opzione è riportato un esempio di una funzionalità fornita da un servizio di linguaggio.  
  
## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minima  
 Il servizio di linguaggio di base contiene i due oggetti seguenti:  
  
-   Il *servizio di linguaggio* implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Un servizio di linguaggio dispone di informazioni sul linguaggio, inclusi il relativo nome, estensioni di file, gestione di finestre di codice e rappresentazione.  
  
-   Il *rappresentazione* implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia.  
  
 Nel disegno concettuale seguente viene illustrato un modello di un servizio di base del linguaggio.  
  
 ![Rappresentazione grafica del modello di servizio di linguaggio](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modello di servizio di linguaggio di base  
  
 Gli host della finestra documento il *vista documento* dell'editor, in questo caso il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale. La visualizzazione del documento e il buffer di testo sono di proprietà dall'editor. Funzionamento di questi oggetti con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite una finestra del documento specializzate chiamata un *finestra del codice*. La finestra del codice è contenuta in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto che viene creato e controllato dall'IDE.  
  
 Quando viene caricato un file con un'estensione specificata, l'editor consente di individuare il servizio di linguaggio associato all'estensione e passa a tale finestra del codice chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo. Il servizio di linguaggio restituisce un *Gestione finestre codice*, che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia.  
  
 Nella tabella seguente viene fornita una panoramica degli oggetti nel modello.  
  
|Componente|Object|Funzione|  
|---------------|------------|--------------|  
|Buffer del testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Un flusso di testo Unicode lettura/scrittura. È possibile che il testo da utilizzare altre codifiche.|  
|Finestra del codice|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Una finestra del documento che contiene uno o più visualizzazioni di testo. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in modalità interfaccia a documenti multipli (MDI), la finestra del codice è un figlio MDI.|  
|Visualizzazione di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Una finestra che consente all'utente di esplorare e visualizzare il testo utilizzando la tastiera e mouse. Una visualizzazione di testo viene visualizzato all'utente come un editor. È possibile utilizzare le visualizzazioni testo normale dell'editor finestre, finestra di Output e finestra di controllo immediato. Inoltre, è possibile configurare uno o più visualizzazioni di testo all'interno di una finestra del codice.|  
|Gestione di testo|Gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> del servizio, da cui ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntatore|Un componente che gestisce le informazioni comuni condivise da tutti i componenti descritti in precedenza.|  
|Servizio di linguaggio|Implementazione dipendenti; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Oggetto che fornisce l'editor con informazioni specifiche della lingua, ad esempio l'evidenziazione della sintassi, il completamento delle istruzioni e corrispondenza delle parentesi graffe.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)