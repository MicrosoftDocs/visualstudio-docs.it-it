---
title: Servizi per linguaggi e l'Editor di componenti di base | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3d2bcad21bb919125b487a57b73d3a458a3a1f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="language-services-and-the-core-editor"></a>Servizi per linguaggi e l'Editor di componenti di base
Editor di Visual Studio sono spesso associati a un servizio di linguaggio. Tra le altre cose, un servizio di linguaggio fornisce la colorazione della sintassi, il completamento delle istruzioni, IntelliSense e la formattazione del testo.  
  
## <a name="core-editors-and-document-data-objects"></a>Editor di componenti di base e gli oggetti dati documento  
 Quando si accede l'editor di componenti di base, non si crea gli oggetti di visualizzazione di documento e di dati del documento. L'IDE crea e controlla questi due oggetti e per ottenere l'handle, effettua le chiamate appropriate nell'editor di implementazione della factory.  
  
 Per ulteriori informazioni, vedere [determinare quale Editor apre un File in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servizi per linguaggi e l'Editor di componenti di base  
 Implementando un servizio di linguaggio, è possibile controllare la modalità di visualizzazione dei dati nella visualizzazione documento. Un servizio di linguaggio fornisce informazioni e il comportamento specifico per una determinata lingua, ad esempio Visual C++. Quando si crea un buffer di testo e determinare l'estensione per il documento che aperto, il buffer di testo determina il servizio di linguaggio associato a questa estensione del nome file da una chiave del Registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. Il pacchetto VSPackage standard durante il caricamento delle procedure quindi carica il pacchetto VSPackage e viene creata un'istanza del servizio di linguaggio.  
  
 Un servizio di linguaggio di base è illustrato nella figura seguente.  
  
 ![Rappresentazione grafica del modello di servizio di linguaggio](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Oggetti servizio editor e della lingua di base  
  
 L'oggetto dati del documento per l'editor di componenti di base viene chiamato un buffer di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto. L'oggetto visualizzazione del documento è una visualizzazione di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto. Questi due oggetti interagiscono tramite il servizio di linguaggio per fornire una visualizzazione unificata dell'editor di componenti di base. Le informazioni dal buffer di testo e il testo di visualizzazione presente in una finestra del documento è chiamato da una finestra del codice. Il documento di finestra di codice è gestito da un gestore di finestra di codice.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornisce un contesto del servizio di linguaggio tramite l'API Legacy](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosting di IntelliSense](../extensibility/intellisense-hosting.md)   
 [Lingue indipendente](../extensibility/contained-languages.md)   
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)