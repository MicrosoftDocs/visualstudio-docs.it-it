---
title: 'Procedura: supportare la struttura in un servizio di linguaggio Legacy | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9880c5c255118478d15f34f9a9245a1c25d97fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: supportare la struttura in un servizio di linguaggio Legacy
La struttura viene utilizzata per espandere o comprimere le diverse aree di testo. Viene utilizzata la struttura possono essere definiti in modo diverso in diverse lingue. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare la struttura, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.  
  
### <a name="to-support-outlining"></a>Per supportare la struttura  
  
1.  Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sull'oggetto servizio del linguaggio.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione per aggiungere nuove aree della struttura corrente della struttura.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Quando un utente seleziona **Comprimi alle definizioni** sul **struttura** menu, le chiamate IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> del servizio di linguaggio.  
  
 Quando questo metodo viene chiamato, l'IDE passa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore (un puntatore a un buffer di testo) e un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntatore alla struttura sessione corrente).  
  
 È possibile chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodo per specificare queste aree in più aree della struttura di `rgOutlnReg` parametro. Il `rgOutlnReg` parametro è un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struttura. Questo processo consente di specificare diverse caratteristiche dell'area nascosto, ad esempio se una determinata area è espanso o compresso.  
  
> [!NOTE]
>  Prestare attenzione nascondere i caratteri di nuova riga. Il testo nascosto deve estendere dall'inizio della prima riga e l'ultimo carattere dell'ultima riga in una sezione, mentre il carattere di nuova riga finale rimarrà visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire supporto di testo nascosto in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)