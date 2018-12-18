---
title: 'Procedura: implementare Trova e Sostituisci meccanismo | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Procedura: implementare Trova e Sostituisci meccanismo
Visual Studio fornisce due modalità di implementazione di ricerca e sostituzione. Uno consiste nel passare a un'immagine di testo alla shell e perché gestisca la ricerca, evidenziazione e la sostituzione di testo. Ciò consente agli utenti di specificare più intervalli di testo. In alternativa, il pacchetto VSPackage può controllare questa funzionalità se stesso. In entrambi i casi è necessario notificare alla shell sulla destinazione corrente e le destinazioni per tutti i documenti aperti.  
  
### <a name="to-implement-findreplace"></a>Per implementare Trova e Sostituisci  
  
1.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaccia in uno degli oggetti restituiti dalle proprietà frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Se si sta creando un editor personalizzato, è necessario implementare questa interfaccia come parte della classe dell'editor personalizzato.  
  
2.  Utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metodo per specificare le opzioni che supporta l'editor e indicare se implementa la ricerca di testo di immagini.  
  
     Se l'editor supporta la ricerca di testo di immagini, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     In caso contrario, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Se si implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metodi, è possibile semplificare le attività di ricerca mediante la chiamata di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>