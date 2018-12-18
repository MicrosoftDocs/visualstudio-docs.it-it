---
title: Modifica delle impostazioni di visualizzazione tramite l'API Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9857daab890c2dd7bf7a799b6dca4d1b74cb9e37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>La modifica delle impostazioni di visualizzazione tramite l'API Legacy
Impostazioni per le funzionalità di editor di componenti di base, quali ritorno a capo automatico, il margine di selezione e lo spazio virtuale, possono essere modificate dall'utente mediante il **opzioni** la finestra di dialogo. Tuttavia, è anche possibile modificare queste impostazioni a livello di codice.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modifica delle impostazioni tramite l'API Legacy  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia espone un set di proprietà dell'editor di testo. Visualizzazione di testo contiene una categoria di proprietà (GUID_EditPropCategory_View_MasterSettings) che rappresenta il gruppo di impostazioni modificate a livello di codice per la visualizzazione del testo. Una volta che le impostazioni di visualizzazione sono state modificate in questo modo, non possono essere modificate nel **opzioni** la finestra di dialogo fino a quando non vengono reimpostate.  
  
 Di seguito è il processo tipico per la modifica delle impostazioni di visualizzazione per un'istanza dell'editor di componenti di base.  
  
1.  Chiamare `QueryInterface` sul (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo, specificando un valore di GUID_EditPropCategory_View_MasterSettings per il `rguidCategory` parametro.  
  
     Questa operazione restituisce un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia, che contiene il set di proprietà forzato per la visualizzazione. Le impostazioni di questo gruppo in modo permanente forzate. Se un'impostazione non è presente in questo gruppo, quindi seguirà le opzioni specificate nel **opzioni** la finestra di dialogo o i comandi dell'utente.  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodo, specificando il valore delle impostazioni appropriate nel `idprop` parametro.  
  
     Per forzare il ritorno a capo automatico, ad esempio, è consigliabile chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> e specificare un valore di VSEDITPROPID_ViewLangOpt_WordWrap, `vt` per il `idprop` parametro. In questa chiamata, `vt` è una variante del tipo VT_BOOL e `vt.boolVal` è VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Ripristino delle impostazioni di visualizzazione modificato  
 Per reimpostare qualsiasi vista modificata l'impostazione per un'istanza dell'editor principale, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> (metodo) e specificare il valore dell'impostazione appropriata nel `idprop` parametro.  
  
 Ad esempio, per consentire di ritorno a capo automatico mobile liberamente, si sarebbe rimuoverlo dalla categoria di proprietà chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e specificando un valore di VSEDITPROPID_ViewLangOpt_WordWrap per il `idprop` parametro.  
  
 Per rimuovere modificate tutte le impostazioni per l'editor di componenti di base in una sola volta, specificare un valore di VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt per il `idprop` parametro. In questa chiamata, vt è una variante del tipo VT_BOOL e vt.boolVal è VARIANT_TRUE.  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)