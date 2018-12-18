---
title: I servizi correlati e le interfacce (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d19c7e2560fafbf54257bf4c46303874bfc717b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfacce (origine controllo VSPackage) e i servizi correlati
Questa sezione vengono elencate tutte le interfacce correlate al pacchetto VSPackage in controllo di origine al [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Il controllo del codice sorgente VSPackage implementa alcune di queste interfacce e altri utilizza per effettuare attività di controllo di origine.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfacce implementate da e per pacchetti VSPackage di controllo di origine  
 Le interfacce seguenti sono descritti nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], e il controllo del codice sorgente VSPackage implementa un sottoinsieme di essi in base al relativo set di funzionalità desiderata. Alcune interfacce sono contrassegnate come obbligatorio e deve essere implementata da ogni controllo del codice sorgente VSPackage.  
  
 Per le interfacce che non implementa un pacchetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'implementazione predefinita. Si noti che l'implementazione predefinita è progettato per il caso, quando non viene registrato alcun VSPackage e non viene controllato alcun progetto. Un controllo del codice sorgente scritto correttamente VSPackage implementa le interfacce necessarie tutti anziché lasciare l'implementazione predefinita di tali interfacce.  
  
 Un controllo del codice sorgente VSPackage deve implementare un servizio privato che incapsula alcune o tutte le interfacce seguenti.  
  
 Le interfacce sono:  
  
-   Richiesto: Dell'entità (progetto di controllo del codice sorgente VSPackage Stub del controllo, origine) deve implementare l'interfaccia.  
  
-   Consigliato: L'entità deve implementare questa interfaccia. controllo del codice sorgente in caso contrario, potrebbe risultare limitato.  
  
-   Facoltativo: l'entità può implementare questa interfaccia per fornire una serie più ricca di funzionalità.  
  
|Interfaccia|Scopo|Implementato da|Implementare?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editor di chiamare questa interfaccia prima di modificare o salvare un file. Il controllo del codice sorgente VSPackage può estrarre il file o nega l'operazione se l'estrazione ha esito negativo.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Questa interfaccia fornisce funzionalità di controllo di origine di base per i progetti, ad esempio la registrazione e annullamento della registrazione per i progetti a controllo del codice sorgente e fornire supporto per i glifi di controllo di origine di base.|Controllo del codice sorgente VSPackage|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Questa interfaccia viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> utilizzando il <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funzione, o semplicemente il cast dell'oggetto che implementa `IVsHierarchy` a `IVsSccProject2`. Viene utilizzato per ottenere i file nel controllo del codice sorgente in un progetto o per informare il progetto dello stato corrente del controllo origine o posizione.|Progetto|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Il modulo di integrazione utilizza questa interfaccia per impostare il pacchetto VSPackage attivo corrente.|Controllo del codice sorgente VSPackage|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Questa interfaccia è basata su un modello di sottoscrizione. Qualsiasi pacchetto VSPackage può segnalare che si desidera ricevere gli eventi del documento ed essere consigliabile dalla shell per gli eventi che stanno per verificarsi. Viene implementata e gestito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], che a sua volta passa gli eventi che implementa il `IVsTrackProjectDocumentsEvents2` al pacchetto VSPackage.|Stub di controllo di origine|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Questa interfaccia fornisce l'elaborazione batch, le operazioni di lettura/scrittura sincronizzato e un avanzato `OnQueryAddFiles` metodo.|Stub di controllo di origine|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Esplora soluzioni** e progetti chiamato questa interfaccia per i progetti vengono aggiunti nuovi file, o quando i file e cartelle vengono rinominate o eliminate da progetti. Il controllo del codice sorgente VSPackage può estrarre il file di progetto o annullare l'operazione.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Esplora soluzioni** e progetti di chiamare questa interfaccia in risposta alle chiamate ai metodi dell'interfaccia IVstrackProjectDocuments3. Operazioni di lettura/scrittura, il controllo del codice sorgente VSPackage può tenere traccia delle operazioni in batch, sincronizzate e di lavoro con più avanzate `OnQueryAddFiles` metodo.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Questa interfaccia fornisce supporto di gestione di integrazione per progetti Web.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Questa interfaccia viene utilizzata per recuperare le descrizioni comandi per i file di controllo del codice sorgente nei progetti.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Questa interfaccia fornisce supporto delle estensioni dello spazio dei nomi.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|Il pacchetto VSPackage Usa questa interfaccia per integrare un'estensione dello spazio dei nomi nel **New**, **aprire**, o **salvare** finestre di dialogo. Di conseguenza, i progetti possono essere automaticamente aggiunto al controllo del codice sorgente durante la creazione o aggiunto al controllo del codice sorgente quando si salva l'operazione è attiva.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|Il pacchetto VSPackage Usa questa interfaccia per definire i glifi aggiuntivi come icone dei controlli di origine per i nodi **Esplora**.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Il **Aggiungi** la finestra di dialogo per i progetti Web usa tale interfaccia. Fornisce metodi per la visualizzazione per un percorso di origine di controllo e per l'apertura di un progetto Web aggiunto in precedenza nel repository del controllo origine in tale posizione.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Questa interfaccia fornisce supporto per il caricamento asincrono (in background) dei progetti dal controllo del codice sorgente.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Questa interfaccia consente ai progetti di controllare lo stato di caricamento asincrono avviato dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Progetto|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Questa interfaccia consente all'IDE di query sul controllo di origine attiva VSPackage. L'IDE di una query il valore delle impostazioni di controllo di origine che hanno un significato, anche quando è presente alcun controllo di origine attiva che VSPackage registrato. Questa interfaccia viene implementata e gestita da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub di controllo di origine|Obbligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Questa interfaccia viene utilizzata durante la registrazione di controllo del codice sorgente VSPackage.|Stub di controllo di origine|Obbligatorio|  
|<xref:EnvDTE.SourceControl>|Questa interfaccia viene utilizzata in automazione. Di conseguenza, espone solo le funzioni che possono essere eseguite senza visualizzare l'interfaccia utente.|Controllo del codice sorgente VSPackage|Facoltativo|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Questa interfaccia viene utilizzata per salvare l'origine delle impostazioni di controllo nel file di soluzione (sln). Le impostazioni includono il percorso di controllo di origine e il flag di stato di controllo di origine.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Questa interfaccia viene utilizzata per salvare le impostazioni di controllo di origine nel file di opzioni (suo Solution) della soluzione. Ciò può includere le impostazioni di controllo origine specifiche dell'utente, ad esempio il percorso di integrazione dell'utente corrente.|Controllo del codice sorgente VSPackage|Consigliato|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Questa interfaccia viene utilizzata per monitorare gli eventi per eseguire operazioni quali l'archiviazione di file di progetto prima della chiusura di soluzioni, o per ottenere i nuovi file dal controllo del codice sorgente quando si apre un progetto.|Controllo del codice sorgente VSPackage|Consigliato|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)