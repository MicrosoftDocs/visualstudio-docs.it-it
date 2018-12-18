---
title: Considerazioni sulle soluzioni create mediante sandbox | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff85f3407fb24d6d49856bb11ff1852c544cad35
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *Soluzioni create mediante sandbox* sono una funzionalità di Microsoft SharePoint 2010 che consente agli utenti di raccolta siti caricare le proprie soluzioni di codice personalizzato. Una soluzione creata mediante sandbox comune è utenti di caricare le proprie Web part.  
  
 Un'applicazione in modalità sandbox di SharePoint viene eseguito in un processo sicuro e monitorato con accesso a una parte della Web farm. Microsoft SharePoint 2010 Usa una combinazione di funzionalità, le raccolte di soluzioni, soluzione di monitoraggio e un framework di convalida per abilitare soluzioni create mediante sandbox.  
  
## <a name="specifying-project-trust-level"></a>Specifica il livello di attendibilità di progetto  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporta soluzioni create mediante sandbox tramite una proprietà booleana del progetto chiamate *soluzione creata mediante sandbox*. Questa proprietà può essere impostata in qualsiasi momento nel progetto o può essere specificato quando si crea il progetto nel **Personalizzazione guidata SharePoint**.  
  
> [!NOTE]  
>  Modifica il *soluzione creata mediante sandbox* proprietà di un progetto dopo averlo creato può causare errori di convalida.  
  
 La soluzione viene considerata una soluzione con ambito farm se la *soluzione creata mediante sandbox* è impostata su **false** o si sceglie il **Distribuisci come soluzione farm** opzione. Tuttavia, la soluzione viene trattata in modo diverso da una soluzione farm se la *soluzione creata mediante sandbox* è impostata su **true** o si sceglie il **Distribuisci come soluzione creata mediante sandbox** opzione della procedura guidata.  
  
## <a name="sharepoint-site-hierarchy"></a>Gerarchia del sito di SharePoint  
 Per informazioni sulle soluzioni come creata mediante sandbox, è opportuno sapere che i siti di SharePoint sono gerarchici nell'ambito. Il primo elemento è noto come Web farm e gli altri elementi sono subordinati:  
  
 Web Farm  
  
 Applicazione Web  
  
 Raccolta siti A1  
  
 Sito A1a  
  
 Applicazione Web B  
  
 Raccolta siti B1  
  
 Sito B1a  
  
 Sito B1b  
  
 Raccolta siti B2  
  
 Sito B2a  
  
 Come si può notare, le Web farm può contenere uno o più applicazioni Web, che a sua volta possono contenere uno o più raccolte siti, che possono avere siti secondari e così via. Modifiche apportate a una raccolta siti influiscono solo tale raccolta e nessun altro. Tuttavia, le modifiche apportate a livello di farm Web influiscono su tutte le raccolte siti nella farm.  
  
 Windows SharePoint Services (WSS) 3.0 consente di distribuire soluzioni solo a livello di farm, ma [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] consente di distribuire a livello di farm (soluzione farm) oppure a livello di raccolta siti (soluzione creata mediante sandbox).  
  
## <a name="why-sandboxed-solutions"></a>Motivo per cui soluzioni create mediante sandbox?  
 WSS 3.0, le soluzioni può essere distribuite solo a livello di farm. In questo modo, che può essere distribuite soluzioni potenzialmente dannose o destabilizzanti che influiscono l'intera Web farm e tutte le altre raccolte siti e applicazioni eseguite in essa contenute. Tuttavia, con le soluzioni create mediante sandbox, è possibile distribuire le soluzioni in un'area secondaria della farm, ovvero una raccolta siti. Per fornire protezione aggiuntiva, l'assembly della soluzione non viene caricato nel principale [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo (w3wp.exe). In alternativa, caricarli in un processo separato (SPUCWorkerProcess.exe). Questo processo viene monitorato e implementa quote e limitazioni per proteggere la farm da soluzioni create mediante sandbox che eseguono attività dannose, ad esempio l'esecuzione di cicli rigidi che utilizzano i cicli della CPU.  
  
## <a name="site-collection-solution-gallery"></a>Soluzioni della raccolta siti  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispone di una funzionalità nota come "raccolta di soluzioni della raccolta siti". È possibile accedere a questa funzionalità dalla pagina Amministrazione centrale SharePoint 2010 o aprendo il **Azioni sito** menu, scegliendo **Impostazioni sito**e quindi scegliendo il **soluzioni** collegamento in **raccolte** nel sito di SharePoint. Le raccolte di soluzioni sono repository di soluzioni che consentono agli amministratori raccolta siti gestire soluzioni nelle proprie raccolte siti.  
  
 La raccolta di soluzioni è una raccolta di documenti archiviata nella radice Web del sito di SharePoint. La raccolta di soluzioni sostituisce i modelli di sito e supporta i pacchetti della soluzione. Quando viene caricato un file di pacchetto (con estensione wsp) di soluzione SharePoint, viene elaborato come una soluzione creata mediante sandbox.  
  
## <a name="sandboxed-solution-limitations"></a>Limitazioni di soluzione creata mediante sandbox  
 Quando si distribuisce una soluzione creata mediante sandbox, la matrice delle funzionalità di SharePoint disponibili per il processo è limitata per ridurre le vulnerabilità di sicurezza di che potrebbe disporre. Alcune di queste limitazioni includono quanto segue:  
  
-   Soluzioni create mediante sandbox sono un subset limitato di elementi di soluzione distribuibili a loro disposizione. Modelli di progetto SharePoint potenzialmente vulnerabili, ad esempio le definizioni di sito e i flussi di lavoro, non sono disponibili.  
  
-   SharePoint esegue codice soluzione creata mediante sandbox in un processo (SPUCWorkerProcess.exe) separato dalla principale [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo (w3wp.exe) di pool di applicazioni.  
  
-   Mapping di cartelle non può essere aggiunto al progetto.  
  
-   Tipi di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft.Office.Server non può essere utilizzato in soluzioni create mediante sandbox. Inoltre, solo i tipi nel [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint può essere utilizzato in soluzioni create mediante sandbox.  
  
 È importante notare che se si specifica una soluzione di SharePoint come una soluzione creata mediante sandbox non ha alcun effetto in SharePoint server. solo determina la modalità del progetto SharePoint viene distribuito in SharePoint da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e gli assembly associati a. Non si applica il file con estensione wsp generati e il file con estensione wsp non contiene dati che è direttamente correlato al *soluzione creata mediante sandbox* proprietà.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funzionalità e gli elementi nelle soluzioni create mediante sandbox  
 Soluzioni create mediante sandbox supportano le funzionalità e gli elementi seguenti:  
  
-   Campi di tipi di contenuto  
  
-   Azioni personalizzate  
  
-   Flussi di lavoro dichiarativi  
  
-   Ricevitori di eventi  
  
-   Funzionalità callout  
  
-   Definizioni di elenco  
  
-   Istanze di elenco  
  
-   Modulo/file  
  
-   Navigazione  
  
-   Onet.Xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Supporto per tutte le Web part che derivano da `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web part  
  
-   Funzionalità webtemplate (anziché webtemp)  
  
-   Web part visive  
  
 Soluzioni create mediante sandbox non supportano le funzionalità e gli elementi seguenti:  
  
-   Pagine dell'applicazione  
  
-   Gruppo di azioni personalizzate  
  
-   Funzionalità con ambito farm  
  
-   elemento `HideCustomAction`  
  
-   Funzionalità con ambito di applicazione Web  
  
-   Flussi di lavoro con codice  
  
## <a name="see-also"></a>Vedere anche  
 [Differenze tra creata mediante sandbox e soluzioni Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  