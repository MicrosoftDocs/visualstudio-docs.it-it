---
title: Implementazione di categorie personalizzate e elementi visualizzati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2dedd54aa1db26e38b6f212c616bd38c09018961
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementazione di elementi visualizzati e categorie personalizzate
Un pacchetto VSPackage può fornire controllo dei tipi di carattere e colori del testo per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) tramite le categorie personalizzate e di elementi visualizzati.  
  
 Categorie personalizzate e gli elementi di visualizzazione si trovano i **tipi di carattere e colori** pagina delle proprietà. Per aprire il **tipi di carattere e colori** nella pagina proprietà di **strumenti** menu, fare clic su **opzioni**. Espandere **ambiente** e quindi fare clic su **tipi di carattere e colori**.  
  
 Quando si utilizza questo meccanismo, i pacchetti VSPackage devono implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e le relative interfacce associate.  
  
 In sostanza, questo meccanismo può essere utilizzato per modificare tutte le **visualizzare gli elementi** e **categorie** che li contengono. Tuttavia, non essere usato per modificare il **testo EditorCategory** o dai relativi **visualizzare gli elementi**. Per ulteriori informazioni, vedere [tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md).  
  
 Per implementare personalizzato **categorie** o **visualizzare gli elementi**, un pacchetto VSPackage deve:  
  
-   Creare o identificare categorie nel Registro di sistema.  
  
     Implementazione dell'IDE del **tipi di carattere e colori** pagina delle proprietà utilizza queste informazioni per eseguire correttamente le query per il servizio supporta una determinata categoria.  
  
-   Creare o identificare i gruppi (facoltativi) nel Registro di sistema.  
  
     Può essere utile definire un gruppo che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce gli elementi di visualizzazione all'interno del gruppo.  
  
-   Implementazione del supporto IDE.  
  
-   Gestire le modifiche di carattere e colori.  
  
 Per informazioni, vedere [accesso archiviati tipo di carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie  
  
-   Creare un tipo speciale di voce del Registro di sistema categoria [HKLM\Software\Microsoft. \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\`<Category>`]  
  
     *\<Categoria >* è il nome non localizzato della categoria.  
  
-   Popolare il Registro di sistema con due valori:  
  
    |nome|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|Un GUID creato per identificare la categoria.|  
    |Pacchetto|REG_SZ|GUID|Il GUID del servizio VSPackage che supporta la categoria.|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> per la categoria corrispondente.  
  
## <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi  
  
-   Creare un tipo speciale di voce del Registro di sistema categoria [HKLM\Software\Microsoft. \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\  *\<gruppo >*]  
  
     *\<gruppo >* è il nome non localizzato del gruppo.  
  
-   Popolare il Registro di sistema con due valori:  
  
    |nome|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|Un GUID creato per identificare il gruppo.|  
    |Pacchetto|REG_SZ|GUID|Il GUID del servizio che supporta la categoria.|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` per il gruppo corrispondente.  
  
## <a name="to-implement-ide-support"></a>Per implementare il supporto IDE  
  
-   Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, che restituisce un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia all'IDE per ciascuna **categoria** o gruppo GUID specificato.  
  
-   Per ogni **categoria** supporta, un VSPackage che implementa un'istanza separata del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia.  
  
-   I metodi implementati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> deve fornire l'IDE con:  
  
    -   Elenchi di **visualizzare gli elementi** nel **categoria.**  
  
    -   Nomi localizzabili per **visualizzare gli elementi**.  
  
    -   Visualizzare le informazioni per ogni membro di **categoria**.  
  
    > [!NOTE]
    >  Ogni **categoria** deve contenere almeno un **elemento visualizzato**.  
  
-   L'IDE Usa il `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia per definire un'unione di diverse categorie.  
  
     L'implementazione fornisce l'IDE con:  
  
    -   Un elenco di **categorie** che costituiscono un gruppo specificato.  
  
    -   Accesso alle istanze del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> supporto ogni **categoria** all'interno del gruppo.  
  
    -   Nomi di gruppo localizzabile.  
  
-   Aggiornamento dell'IDE:  
  
     L'IDE memorizza nella cache di informazioni sulle **carattere e colori** impostazioni. Di conseguenza, dopo l'eventuale modifica dell'IDE **carattere e colori** configurazione, è consigliabile assicurarsi che la cache è aggiornata.  
  
 Aggiornamento della cache viene eseguita tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> l'interfaccia e può essere eseguita a livello globale o solo in elementi.  
  
## <a name="to-handle-font-and-color-changes"></a>Per gestire i tipi di carattere e colore le modifiche  
 Per supportare correttamente la colorazione di testo che visualizza un VSPackage, il servizio di colorazione supporta il pacchetto VSPackage deve rispondere alle modifiche avviata dall'utente tramite il **tipi di carattere e colori** pagina delle proprietà. Un pacchetto VSPackage a tale scopo:  
  
-   Gestione degli eventi generati da IDE implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaccia.  
  
     L'IDE chiama il metodo appropriato, le modifiche apportate dall'utente di seguenti il **tipi di carattere e colori** pagina. Ad esempio, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodo se si seleziona un nuovo tipo di carattere.  
  
     oppure  
  
-   L'IDE per le modifiche di polling.  
  
     Questo può avvenire tramite implementato dal sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia. Sebbene principalmente per il supporto di persistenza, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metodo può essere utilizzato per ottenere informazioni di carattere e colori per **visualizzare gli elementi**. Per ulteriori informazioni, vedere [accesso archiviati tipo di carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Per garantire che i risultati ottenuti tramite polling siano corretti, potrebbe essere utile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se sono necessari un scaricamento della cache e l'aggiornamento prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Recupero di tipo di carattere e colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L'accesso a carattere archiviato e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Procedura: accedere ai tipi di carattere incorporati e una combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Panoramica di colore e tipo di carattere](../extensibility/font-and-color-overview.md)