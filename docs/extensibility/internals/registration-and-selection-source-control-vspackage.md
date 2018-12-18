---
title: Registrazione e la selezione (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b0f02abe4cad58db27700aee3c29ec8d2dd7a7e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e la selezione (origine controllo VSPackage)
Un pacchetto VSPackage deve essere registrato per esporla a controllo del codice sorgente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se più di un controllo del codice sorgente VSPackage è registrato, l'utente può selezionare il pacchetto VSPackage per caricare in momenti appropriati. Vedere [VSPackage](../../extensibility/internals/vspackages.md) per ulteriori dettagli sul VSPackage e come eseguirne la registrazione.  
  
## <a name="registering-a-source-control-package"></a>Registrazione di un pacchetto di controllo di origine  
 Il pacchetto di controllo di origine viene registrato in modo che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente possa trovare e query per le funzionalità supportate. Ciò è conforme a uno schema di caricamento ritardato in cui viene creata un'istanza di un pacchetto solo quando la funzionalità o i comandi sono necessari o vengono richiesti in modo esplicito.  
  
 Pacchetti VSPackage inseriscono informazioni di una chiave del Registro di sistema specifiche della versione, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *X* è il numero di versione principale e *Y* è il numero di versione secondario. Questo metodo assicura la possibilità di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI) supporta la selezione tra più codice sorgente installato controllo plug-in (tramite il pacchetto di scheda di controllo di origine) e controllo del codice sorgente VSPackage. Può esistere un solo plug-in controllo del codice sorgente active o VSPackage alla volta. Tuttavia, come descritto di seguito, l'IDE consente di passare tra plug-in del controllo codice sorgente e i package VS tramite un automatico meccanismo effettuare lo swapping del pacchetto di soluzione in base. Esistono alcuni requisiti per il controllo del codice sorgente VSPackage per abilitare questo meccanismo di selezione.  
  
### <a name="registry-entries"></a>Voci del Registro di sistema  
 Un pacchetto di controllo di origine deve tre GUID privato:  
  
-   GUID del pacchetto: Questo è il GUID principale per il pacchetto che contiene l'implementazione del controllo origine (denominato ID_Package in questa sezione).  
  
-   Controllo del codice sorgente GUID: Questo è un GUID per il controllo del codice sorgente utilizzato per registrare lo Stub di controllo di Visual Studio origine VSPackage e viene usato anche come un comando dell'interfaccia utente il GUID di contesto. Il servizio di controllo GUID di origine è registrato sotto il controllo del codice sorgente GUID. Nell'esempio, il controllo del codice sorgente GUID tratta ID_SccProvider.  
  
-   GUID del servizio controllo di origine: si tratta del servizio privato GUID utilizzato da Visual Studio (denominato SID_SccPkgService in questa sezione). Oltre a ciò, il pacchetto di controllo di origine deve definire altri GUID per pacchetti VSPackage, finestre degli strumenti e così via.  
  
 Le seguenti voci del Registro di sistema devono essere effettuate da un controllo del codice sorgente VSPackage:  
  
|Nome della chiave|Voci|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(predefinito) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(predefinito) = rg_sz:\<nome descrittivo del pacchetto ><br /><br /> Servizio = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(predefinito) = rg_sz: #\<ID di risorsa per nome localizzato ><br /><br /> Pacchetto = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Si noti che il nome della chiave, `SourceCodeControl`, è già utilizzato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e non è disponibile come scelta per \<PackageName >.)|(predefinito) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto di controllo di origine  
 Diverse basate su API plug-in origine controllo plug-in e possono essere registrati contemporaneamente pacchetti VSPackage di controllo del codice sorgente. Verificare che il processo di selezione di un plug-in controllo del codice sorgente o un pacchetto VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica il plug-in o VSPackage al momento appropriato e rinviare il caricamento di componenti non necessari fino a quando non sono necessarie. Inoltre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve rimuovere l'interfaccia utente da altri pacchetti VSPackage inattivo, tra cui le voci di menu, finestre di dialogo e barre degli strumenti e visualizzare l'interfaccia utente per il pacchetto VSPackage attivo.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Carica un controllo del codice sorgente VSPackage quando viene eseguita una qualsiasi delle operazioni seguenti:  
  
-   Soluzione viene aperta (quando la soluzione è inclusa nel controllo del codice sorgente).  
  
     Quando viene aperta una soluzione o progetto incluso nel controllo del codice sorgente, l'IDE determina il controllo del codice sorgente VSPackage che è stato designato per tale soluzione deve essere caricata.  
  
-   Vengono eseguiti i comandi di menu del controllo origine pacchetto VSPackage.  
  
 Un controllo del codice sorgente che VSPackage deve caricare tutti i componenti che necessari solo quando effettivamente dovranno essere utilizzato (in caso contrario noto come caricamento ritardato).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Lo scambio automatico VSPackage basati su una soluzione  
 È possibile scambiare manualmente i pacchetti VSPackage controllo del codice sorgente tramite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opzioni** nella finestra di dialogo di **controllo del codice sorgente** categoria. La sostituzione automatica di pacchetti basati su una soluzione significa che un pacchetto di controllo di origine che è stato designato per una particolare soluzione viene automaticamente impostato su attivo quando tale soluzione è aperta. Ogni pacchetto di controllo di origine deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gestisce il passaggio tra sia del codice sorgente plug-in del controllo (implementa l'API plug-in controllo di origine) e VSPackage di controllo del codice sorgente.  
  
 Il pacchetto di scheda di controllo di origine viene utilizzato per passare a qualsiasi basate su API plug-in controllo di origine del plug-in. Il processo di passaggio per il pacchetto intermedia della scheda controllo origine e determinare quale plug-in controllo del codice sorgente deve essere impostato su Attiva o inattiva è trasparente all'utente. Il pacchetto di Adapter è sempre attivo quando è attiva qualsiasi plug-in controllo del codice sorgente. Passaggio tra due gli importi di plug-in controllo origine semplicemente durante il caricamento e scaricamento di DLL plug-in. Passaggio a un controllo del codice sorgente VSPackage, tuttavia, comporta l'interazione con l'IDE a caricare il pacchetto VSPackage appropriato.  
  
 Un controllo del codice sorgente VSPackage viene chiamato quando viene aperta una soluzione e la chiave del Registro di sistema per il pacchetto VSPackage è nel file di soluzione. Quando viene aperta la soluzione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva che il valore del Registro di sistema e carica il controllo del codice sorgente appropriato VSPackage. Controllo del codice sorgente tutti i pacchetti VSPackage deve avere le voci del Registro di sistema descritte in precedenza. Una soluzione nel controllo del codice sorgente viene contrassegnata come viene associata a un controllo del codice sorgente VSPackage. I pacchetti VSPackage devono implementare controllo del codice sorgente di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> per abilitare automatico basato su soluzione VSPackage la sostituzione.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaccia utente per la selezione di pacchetto e passare a Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un'interfaccia utente per controllo del codice sorgente VSPackage e selezione plug-nel **opzioni** nella finestra di dialogo di **controllo del codice sorgente** categoria. Consente all'utente di selezionare il controllo del codice sorgente active plug-in o di un pacchetto VSPackage. Include un elenco a discesa:  
  
-   Tutti i pacchetti di controllo codice sorgente installato  
  
-   Tutti i plug-in controllo codice sorgente installato  
  
-   "none" opzione che consente di disattivare controllo del codice sorgente  
  
 L'interfaccia utente per la scelta del controllo origine attiva è visibile. La selezione di VSPackage nasconde l'interfaccia utente per il pacchetto VSPackage precedente e viene illustrata l'interfaccia utente per una nuova. Il pacchetto VSPackage active è selezionato in ogni utente. Se un utente dispone di più copie di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aperte contemporaneamente, ognuno di essi può usare un pacchetto VSPackage active diversi. Se più utenti sono connessi allo stesso computer, ogni utente può avere istanze separate di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aprire, ognuno con un pacchetto VSPackage active diversi. Quando più istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siano chiusi da un utente, il controllo del codice sorgente VSPackage che era attivo per l'ultima soluzione aperta diventa il controllo del codice sorgente predefinito VSPackage, da impostare attivo per il riavvio.  
  
 A differenza delle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], riavviare l'IDE non è più l'unico modo per passare a controllo del codice sorgente VSPackage. Selezione di VSPackage è automatica. Commutazione di pacchetti richiede privilegi di utente di Windows (non Administrator o Power User).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)   
 [Creazione di plug-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)