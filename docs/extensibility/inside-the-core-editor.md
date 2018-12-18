---
title: Nell'Editor di componenti di base | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95745cbef015e9f6ceddb9b84d75b52ec9805dea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="inside-the-core-editor"></a>Nell'Editor di componenti di base
Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale è un set di diversi componenti che consentono di modificare ed eseguire query su informazioni testuali. Se l'editor di componenti di base è stato personalizzato utilizzando l'API legacy, è possibile continuare a usare queste personalizzazioni, verranno instradate tramite le schede dell'editor. Si consiglia, tuttavia, che si adattano le personalizzazioni per il nuovo editor API.  
  
 Di seguito sono riportati alcuni aspetti importanti dell'editor principale:  
  
-   Buffer del testo  
  
-   Visualizzazione di testo  
  
-   Finestra del codice  
  
-   Marcatori di testo  
  
-   Gestione di testo  
  
-   Integrazione con servizi di linguaggio  
  
## <a name="in-this-section"></a>In questa sezione  
 [Creazione di istanze di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare un'istanza di base dell'editor.  
  
 [Accesso ai Buffer di testo tramite l'API Legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Viene descritto il ruolo del buffer di testo nell'editor di componenti di base, vengono illustrati i sistemi associati vengono utilizzati per accedere al buffer e viene fornito un elenco delle interfacce implementate dall'oggetto buffer di testo, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventi nel Buffer di testo nell'API Legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fornisce un elenco delle interfacce che vengono utilizzati per la notifica degli eventi del buffer di testo.  
  
 [Procedura: eseguire la registrazione per gli eventi nel Buffer di testo con l'API Legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Descrive come informare gli eventi nel buffer di testo.  
  
 [Utilizzando la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato come utilizzare la gestione di testo per condividere informazioni relative alle preferenze globali con i componenti di base dell'editor e come ricevere la notifica degli eventi di gestione di testo.  
  
 [L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Viene descritto il ruolo della visualizzazione del testo nell'editor di componenti di base ed elenca le interfacce implementate dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 [Personalizzazione di codice Windows tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fornisce informazioni su come una finestra del codice viene usata per delimitare la visualizzazione del testo, viene illustrato come utilizzare la gestione di finestre di codice per fornire le decorazioni alla finestra del codice e fornisce una notifica di nuove visualizzazioni.  
  
 [La modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come forzare le impostazioni di visualizzazione e su come rimuovere le impostazioni forzate.  
  
 [Servizi per linguaggi e l'Editor di componenti di base](../extensibility/language-services-and-the-core-editor.md)  
 Descrive la creazione dell'istanza di un servizio di linguaggio per effetti di codice di controllo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Vengono fornite istruzioni dettagliate su come avviare l'editor di componenti di base da codice gestito.  
  
 [Barra dei menu a discesa](../extensibility/drop-down-bar.md)  
 Viene spiegato come viene usata nella finestra del codice e vengono descritte le interfacce che vengono utilizzate quando si implementa una barra dei menu a discesa della barra dei menu a discesa.  
  
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Viene illustrato il concetto di marcatori di testo e come vengono usati nell'editor di componenti di base ed elenca le interfacce che consentono di accedere e gestire i marcatori di testo.  
  
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un indicatore di testo e come aggiungere un comando personalizzato a un menu di scelta rapida.  
  
 [Procedura: creare marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un indicatore di testo personalizzato e come fornire il tipo di marcatore come servizio.