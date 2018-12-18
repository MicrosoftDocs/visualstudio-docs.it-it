---
title: L'accesso a carattere archiviato e le impostazioni dei colori | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4dec66fca6061601c4bc02389605d140ee3bb81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-stored-font-and-color-settings"></a>L'accesso a carattere archiviato e le impostazioni dei colori
Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) vengono archiviate le impostazioni modificate per i tipi di carattere e colori nel Registro di sistema. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia per accedere a queste impostazioni.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Per avviare la persistenza dello stato dei tipi di carattere e colori  
 Informazioni di carattere e colori vengono archiviate in base alla categoria nel percorso seguente del Registro di sistema: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\  *\<CategoryGUID >*], dove  *\<CategoryGUID >* è il GUID di categoria.  
  
 Pertanto, per avviare la persistenza, un pacchetto VSPackage deve:  
  
-   Ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia chiamando `QueryService` sul provider del servizio globale.  
  
     `QueryService`deve essere chiamato con un argomento di ID servizio di `SID_SVsFontAndColorStorage` e un argomento di ID di interfaccia di `IID_IVsFontAndColorStorage`.  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> per aprire una categoria per essere resa persistente usando il GUID della categoria e un flag di modalità come argomenti.  
  
     La modalità, specificata da di `fFlags` argomento, viene costruito dai valori di <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumerazione. Questa modalità controlli:  
  
    -   Le impostazioni che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Tutte le impostazioni o solo quelli che gli utenti di modificare e che sono recuperabili tramite le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Le modalità di propagazione delle modifiche alle impostazioni utente.  
  
    -   Il formato dei valori di colore che vengono utilizzati.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Per utilizzare la persistenza dello stato dei tipi di carattere e colori  
 Persistenza dei tipi di carattere e colori include:  
  
-   Le impostazioni IDE. la sincronizzazione con le impostazioni archiviate nel Registro di sistema.  
  
-   Propagazione delle informazioni sulla modifica del Registro di sistema.  
  
-   L'impostazione e recupero delle impostazioni archiviate nel Registro di sistema.  
  
 La sincronizzazione all'impostazione di archiviazione con le impostazioni IDE è trasparente. L'IDE sottostante scrive automaticamente le impostazioni aggiornate per **elementi visualizzati** alle voci del Registro di sistema di categorie.  
  
 Se più pacchetti VSPackage condividono una categoria specifica, un pacchetto VSPackage richiede che gli eventi vengono generati quando i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia vengono utilizzati per modificare le impostazioni del Registro di sistema archiviate.  
  
 Per impostazione predefinita, non è abilitata la generazione di eventi. Per abilitare la generazione di eventi, è necessario aprire una categoria utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. In questo modo, l'IDE chiamare appropriata <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodo che implementa un pacchetto VSPackage.  
  
> [!NOTE]
>  Modifica dei dati mediante il **carattere e colori** pagina delle proprietà generano eventi indipendenti <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario eseguire un aggiornamento delle impostazioni di carattere e colori memorizzati nella cache prima di chiamare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.  
  
### <a name="storing-and-retrieving-information"></a>L'archiviazione e recupero delle informazioni  
 Per ottenere o configurare le informazioni che un utente può modificare per un elemento di visualizzazione denominata in una categoria aperto, chiamare i pacchetti VSPackage di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metodi.  
  
 Gli attributi di informazioni sui tipi di carattere per una particolare categoria verrà ottenuta tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metodi.  
  
> [!NOTE]
>  Il `fFlags` argomento passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo all'apertura di tale categoria definisce il comportamento del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metodi. Per impostazione predefinita, questi itemsthat aboutdisplay di metodi restituiscono solo le informazioni sono state modificate. Tuttavia, se viene aperto con una categoria di <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> flag sia aggiornato e gli elementi di visualizzazione invariato accessibili da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Per impostazione predefinita, solo modificato **elementi visualizzati** informazioni vengono mantenute nel Registro di sistema. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia non può essere utilizzata per recuperare tutte le impostazioni per i tipi di carattere e colori.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> restituiscono REGDB_E_KEYMISSING, (0x80040152L) quando vengono utilizzati per recuperare informazioni su unchanged **elementi visualizzati**.  
  
 Le impostazioni di tutte **elementi visualizzati** in un particolare **categoria** può essere ottenuto utilizzando i metodi del `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementazione di elementi visualizzati e categorie personalizzate](../extensibility/implementing-custom-categories-and-display-items.md)