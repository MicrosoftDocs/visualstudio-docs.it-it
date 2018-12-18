---
title: Creazione di cartelle dei contenitori padre per soluzioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2104c0c109db0d410cbd08683ce227c62982fd65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-parent-container-folders-for-solutions"></a>Creazione di cartelle dei contenitori padre per le soluzioni
Nell'API versione 1.2 del plug-in controllo di origine, un utente può specificare una destinazione di controllo di origine solo nodo radice per tutti i progetti Web all'interno della soluzione. Questa singola radice viene chiamata una radice unificata Super (SUR).  
  
 Nell'API versione 1.1 del plug-in controllo di origine, se l'utente aggiunto una soluzione multiprogetto al controllo del codice sorgente, l'utente è stato richiesto di specificare una destinazione di controllo di origine per ogni progetto Web.  
  
## <a name="new-capability-flags"></a>Nuovo flag di capacità  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quasi sempre creata una cartella SUR durante l'aggiunta di una soluzione a controllo del codice sorgente. In particolare, esegue l'operazione nei casi seguenti:  
  
-   Il progetto è una condivisione file di progetto Web.  
  
-   Esistono unità differenti per il progetto e il file della soluzione.  
  
-   Sono disponibili diverse azioni per il progetto e il file della soluzione.  
  
-   Progetti sono stati aggiunti separatamente (in una soluzione di controllo del codice sorgente).  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è consigliabile che il nome della cartella SUR coincidere con il nome della soluzione senza l'estensione. Nella tabella seguente viene riepilogato il comportamento in due versioni.  
  
|Funzionalità|tSource controllo plug-in API versione 1.1|API plug-in versione 1.2 di controllo del codice sorgente|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Aggiungi soluzione al controllo del codice sorgente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Aggiungere un progetto alla soluzione di controllo del codice sorgente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Nota:** Visual Studio si presuppone che una soluzione è un figlio diretto del sur il.|  
  
## <a name="examples"></a>Esempi  
 Nella tabella seguente sono elencati due esempi. In entrambi i casi, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente viene richiesto un percorso di destinazione per la soluzione nel controllo del codice sorgente finché il *user_choice* viene specificato come destinazione. Quando viene specificato il user_choice, senza chiedere conferma all'utente per le destinazioni di controllo di origine vengono aggiunti alla soluzione e due progetti.  
  
|Soluzione contiene|In percorsi su disco|Struttura del database predefinito|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 Cartella SUR e delle sottocartelle vengono create indipendentemente dal fatto che l'operazione è stata annullata o ha esito negativo a causa di un errore. Vengono automaticamente rimossi nelle condizioni di errore o annullamento.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valore predefinito è la versione 1.1 comportamento se il plug-in del controllo del codice sorgente non restituisce `SCC_CAP_CREATESUBPROJECT` e `SCC_CAP_GETPARENTPROJECT` flag di capacità. Inoltre, gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile scegliere di ripristinare il comportamento della versione 1.1 impostando il valore della seguente chiave su DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)