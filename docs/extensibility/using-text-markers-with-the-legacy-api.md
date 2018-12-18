---
title: Utilizzo degli indicatori di testo con l'API Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98c889bc1bc128a941f726348781a633799475de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>Utilizzo degli indicatori di testo con l'API Legacy
Un indicatore di testo è un intervallo di testo in un buffer che può influenzare la visualizzazione a virgola mobile e il comportamento di un'area di testo. Marcatori di includono i punti di interruzione, segnalibri, sottolineature ondulate di colore e le aree di sola lettura. I marcatori di testo sono fondamentalmente diversi da colorazione della sintassi. La colorazione della sintassi è un modo rapido per comunicare la sintassi del linguaggio che è associata a un'area di testo. La colorazione della sintassi in genere è richiesta quando Windows ridisegna la schermata, quando la velocità è importante. La colorazione della sintassi cambia solo il colore del testo. Marcatori di testo è possono modificare molte altre proprietà di testo. Marcatori di testo è possono "float" e applicare un comportamento speciale e la colorazione.  
  
 A causa dell'overhead di prestazioni associati agli indicatori di testo, non creare molti marcatori per i buffer di testo. Ogni indicatore viene aggiornato ogni volta che un utente modifica il contenuto del buffer.  
  
> [!NOTE]
>  Gli utenti possono modificare il colore di un tipo di marcatore visibili, ma non la forma e lo stile. Per ulteriori informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)|Viene descritto come aggiungere un tipo di marcatore di testo standard fornito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di componenti di base per una visualizzazione di testo.|  
|[Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)|Viene descritto come implementare un'istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] marcatore utilizzato per indicare gli errori con una sottolineatura ondulata di colore rossa.|  
|[Procedura: creare marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)|Viene descritto come creare e aggiungere un tipo di marcatore di testo personalizzato a una visualizzazione di testo.|  
|[Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)|Viene illustrato come aggiungere marcatori di testo.|  
|[Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)|Vengono descritte le funzionalità dell'editor di componenti di base e vengono fornite informazioni dettagliate su come personalizzare l'editor di componenti di base.|  
|[Funzionalità dell'editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Vengono descritte le funzionalità disponibili nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornisce un meccanismo uniforme per ottenere informazioni su un tipo di marcatore di testo specifico, se predefiniti dall'editor o registrato da un pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fornisce l'accesso a e consente di regolare la posizione di un indicatore di testo in un buffer di testo usando le coordinate bidimensionali.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornisce metodi per la gestione dei marcatori di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornisce i callback per la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE e gli altri processi che consentono di modificare un indicatore di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende le funzionalità disponibili tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende le funzionalità disponibili tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaccia fornendo callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Consente a un tipo di marcatore determinare se altri tipi di marcatore che condividono lo stesso set di colori.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornisce contesto per i marcatori di testo nell'editor di componenti di base. Per ogni tipo di marcatore di testo che è nell'editor di componenti di base, l'IDE crea un oggetto separato <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> oggetto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un gestore che viene fornito per i marcatori di cui glifi supportano la modifica di trascinamento e rilascio. Un'icona è un'icona che indica la posizione di un marcatore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaccia da un servizio che fornisce un testo marcatori altri pacchetti VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fornisce l'accesso a e consente di regolare la posizione di un indicatore di testo in un buffer di testo usando le coordinate unidimensionale. Se possibile, non utilizzare questa interfaccia.