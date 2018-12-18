---
title: Sintassi a colori negli editor personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8c40538b34c23e88b2c680db170b9d46b7b40f62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="syntax-coloring-in-custom-editors"></a>Sintassi colorazione nell'editor personalizzati
Editor di Visual Studio SDK di ambiente, incluso l'editor di componenti di base, utilizzare servizi di linguaggio per identificare elementi sintattici specifici e visualizzarli con i colori specificati per la visualizzazione di un documento specificato.  
  
## <a name="colorization-requirements"></a>Requisiti di colorazione  
 Tutti gli editor di implementazione della rappresentazione di un servizio di linguaggio devono:  
  
1.  Utilizzare un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per gestire il testo da colorati e un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per fornire un documento di visualizzazione del testo.  
  
2.  Ottenere un'interfaccia per un servizio di linguaggio specifico eseguendo query sul provider di servizio del pacchetto VSPackage usando GUID di identificazione del servizio lingue.  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Questo metodo associa il servizio di linguaggio con il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementazione che utilizza il pacchetto VSPackage per gestire il testo che deve essere colorati.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo dell'Editor di componenti di base della rappresentazione di un servizio di linguaggio  
 Quando un servizio di linguaggio con una rappresentazione viene ottenuto da un'istanza dell'editor principale, l'analisi e il rendering del testo per la rappresentazione di un servizio di linguaggio si verifica automaticamente senza richiedere alcun ulteriore intervento da parte dell'utente.  
  
 L'IDE in modo trasparente:  
  
-   Chiama la rappresentazione in base alle esigenze per analizzare e analizzare il testo viene aggiunto o modificato nell'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Assicura che la visualizzazione fornita per la visualizzazione del documento fornita dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementazione viene aggiornata e ridisegnata utilizzando le informazioni restituite dalla rappresentazione.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo di Editor non di base della rappresentazione di un servizio di linguaggio  
 Le istanze dell'editor di componenti di base non può utilizzare anche servizio colorazione di sintassi di un servizio di linguaggio, ma devono in modo esplicito recuperare e applicare la rappresentazione del servizio e aggiornare le visualizzazioni dei documenti stessi.  
  
 A tale scopo, è necessario un editor non di base per:  
  
1.  Ottenere l'oggetto di rappresentazione di un servizio di linguaggio (che implementa l'interfaccia `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Il pacchetto VSPackage esegue questa operazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo nell'interfaccia del servizio di linguaggio.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per richiedere che un determinato intervallo di testo colorati.  
  
     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo restituisce una matrice di valori, uno per ogni lettera nel testo span viene colorato. Identifica, inoltre, l'intervallo di testo come un particolare tipo di elemento colorabile predefinito, ad esempio un commento, parola chiave o tipo di dati.  
  
3.  Utilizzare le informazioni di colorazione restituite da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per aggiornare e visualizzare il testo.  
  
> [!NOTE]
>  Oltre a utilizzare la rappresentazione di un servizio di linguaggio, un pacchetto VSPackage può scegliere di utilizzare il meccanismo di colorazione della sintassi testo Environment SDK di Visual Studio generico. Per ulteriori informazioni su questo meccanismo, vedere [utilizzando tipi di carattere e colori](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [In un servizio di linguaggio Legacy colorazione sintassi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)   
 [Procedura: usare elementi di colori predefiniti](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md)