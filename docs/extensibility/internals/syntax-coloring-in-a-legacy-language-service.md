---
title: Sintassi colorazione in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd740c437fc7e5f3d355e883d4023bc6edfcde1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>In un servizio di linguaggio Legacy colorazione sintassi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza un servizio di colori per identificare gli elementi del linguaggio e visualizzarli con i colori specificati in un editor.  
  
## <a name="colorizer-model"></a>Modello di rappresentazione  
 Il servizio di linguaggio implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia, che viene quindi utilizzato dall'editor. Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente.  
  
 ![SVC rappresentazione grafica](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modello semplice rappresentazione  
  
> [!NOTE]
>  Il servizio di colorazione della sintassi è separato dal generale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meccanismo per la colorazione del testo. Per ulteriori informazioni generali [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] meccanismo supporto colorare, vedere [utilizzando tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
 Oltre alla rappresentazione, il servizio di linguaggio può fornire gli elementi di colori personalizzati che vengono utilizzati dall'editor per la pubblicità che fornisce gli elementi di colori personalizzati. È possibile farlo mediante l'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia sullo stesso oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Restituisce il numero di elementi di colori personalizzati quando si chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (metodo) e restituisce un singolo elemento colorabile predefinito quando si chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (metodo).  
  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo restituisce un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia. Se il servizio di linguaggio supporta i valori di colore a 24 bit o elevato, è necessario implementare la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia sull'oggetto stesso come il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfaccia.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Come un pacchetto VSPackage Usa una rappresentazione di servizio di linguaggio  
  
1.  Il pacchetto VSPackage deve ottenere il servizio di linguaggio appropriato, che richiede il servizio di linguaggio VSPackage di eseguire le operazioni seguenti:  
  
    1.  Utilizzare un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia da ottenere il testo da colorati.  
  
         Il testo viene in genere visualizzato tramite un oggetto che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.  
  
    2.  Ottenere il servizio di linguaggio per il provider del servizio del pacchetto VSPackage per il GUID del servizio di linguaggio di query. Servizi di linguaggio vengono identificati nel Registro di sistema dall'estensione di file.  
  
    3.  Associare il servizio di linguaggio con il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chiamando il relativo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo.  
  
2.  Il pacchetto VSPackage può ora ottenere e utilizzare l'oggetto di rappresentazione, come indicato di seguito:  
  
    > [!NOTE]
    >  Package VS che utilizzano l'editor di componenti di base non è necessario ottenere una lingua in modo esplicito gli oggetti di rappresentazione del servizio. Non appena un'istanza dell'editor di componenti di base Ottiene un servizio di linguaggio appropriato, esegue tutte le attività di colorazione illustrate di seguito.  
  
    1.  Ottenere l'oggetto di rappresentazione del servizio di linguaggio, che implementa il `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfacce, chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo del servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> oggetto.  
  
    2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per ottenere le informazioni di rappresentazione per un determinato intervallo di testo.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Restituisce una matrice di valori, uno per ogni carattere nell'intervallo di testo viene colorato. I valori sono gli indici in un elenco di elemento colorabile predefinito che è l'elenco elemento colorabile predefinito mediante l'editor di componenti di base o un elenco di elemento colorabile gestito dal servizio di linguaggio stesso.  
  
    3.  Utilizzare le informazioni di colorazione restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per visualizzare il testo selezionato.  
  
> [!NOTE]
>  Oltre a usare una rappresentazione di servizio di linguaggio, un VSPackage può usare anche il generico [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colore meccanismo di testo. Per ulteriori informazioni su questo meccanismo, vedere [utilizzando tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)  
 Viene illustrato come un editor accede a un servizio di linguaggio colorazione della sintassi e il servizio di linguaggio deve implementare per supportare la sintassi della colorazione.  
  
 [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Viene illustrato come utilizzare gli elementi di colori predefiniti dal servizio di linguaggio.  
  
 [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)  
 Viene illustrato come implementare gli elementi di colori personalizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md)