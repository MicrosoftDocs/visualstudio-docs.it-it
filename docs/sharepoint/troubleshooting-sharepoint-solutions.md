---
title: Risoluzione dei problemi delle soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba8f84db31cbe41e8bd3f62a7806de0a6d2ea58e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-sharepoint-solutions"></a>Risoluzione dei problemi relativi alle soluzioni SharePoint
  Potrebbero verificarsi i problemi o gli avvisi seguenti durante il debug di soluzioni SharePoint tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger. Per ulteriori informazioni, vedere [debug delle soluzioni di flusso di lavoro di SharePoint 2007](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrizioni dei token nelle web part visive create mediante sandbox  
 Tramite le web part visive nelle soluzioni create mediante sandbox non è possibile elaborare i token standard, ad esempio $SPUrl, supportati dal runtime di SharePoint. Di conseguenza, l'URL non viene risolto e non è possibile visualizzare in anteprima il contenuto nella visualizzazione Progettazione nella finestra di progettazione di web part visive se vi si fa riferimento direttamente in un elemento dello script, come nell'esempio seguente:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Per risolvere questa limitazione e il token, farvi riferimento tramite valori letterali:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrizioni relative ai caratteri in nomi di progetti e di elementi di progetto  
 Nei nomi di progetti e di elementi di progetto possono essere inclusi solo caratteri che sono validi in un percorso di distribuzione in SharePoint 2010. Altri caratteri non consentiti.  
  
### <a name="error-message"></a>Messaggio di errore  
 Messaggio di errore "Caratteri non validi".  
  
### <a name="resolution"></a>Risoluzione  
 Per i nomi di progetti e di elementi di progetto di SharePoint, utilizzare solo i caratteri seguenti:  
  
-   Caratteri ASCII alfanumerici  
  
-   Spazio  
  
-   Punto (.)  
  
-   Virgola ()  
  
-   Carattere di sottolineatura (_)  
  
-   Trattino (-)  
  
-   Barra rovesciata (\\)  
  
 Quando viene creato un pacchetto di un progetto, tramite una regola di convalida viene verificato che nella proprietà del percorso di distribuzione per ogni file distribuito siano contenuti solo questi caratteri validi.  
  
## <a name="errors-when-creating-custom-fields"></a>Errori durante la creazione di campi personalizzati  
 I campi personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono definiti in XML. Si possono verificare errori se un campo non è definito o non vi viene fatto riferimento tramite un formato specifico.  
  
### <a name="error-message"></a>Messaggio di errore  
 Messaggio di errore "Caratteri non validi" in fase di creazione del pacchetto.  
  
### <a name="resolution"></a>Risoluzione  
 L'ID per una definizione di campo deve essere un GUID racchiuso tra parentesi graffe, come illustrato nell'esempio seguente:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Come illustrato nell'esempio seguente, un riferimento di campo in un tipo di contenuto deve essere definito utilizzando il formato di elemento vuoto (\<FieldRef / >), non tramite elementi iniziali o finali (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Se il codice XML di origine per il campo non è corretto, ad esempio un file XML non è valido o presenta altri problemi, si verificherà l'errore indicante che non è possibile analizzare il file.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Le nuove definizioni di sito Non in lingua inglese non vengono visualizzati nella pagina di creazione del sito dopo la distribuzione  
 Dopo aver creato e distribuire una definizione di sito utilizzando una versione inglese di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (ovvero, una versione con impostazioni locali [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] diverso da 1033), il **personalizzazioni di SharePoint** scheda non verrà visualizzata nel **Selezione modello** casella e il nuovo modello di sito non viene visualizzato nel **nuovo sito di SharePoint** pagina.  
  
### <a name="error-message"></a>Messaggio di errore  
 Nessuno.  
  
### <a name="resolution"></a>Risoluzione  
 Questo problema si verifica a causa di un valore non corretto nel **percorso** proprietà per il file di configurazione definizione sito webtemp, ad esempio webtemp_SiteDefinitionProject1. Nel **percorso** proprietà per il file webtemp, sotto il **percorso di distribuzione**, modificare le impostazioni locali 1033 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ad esempio, per l'utilizzo delle impostazioni locali giapponesi modificare il valore su 1041. Per ulteriori informazioni, vedere [ID impostazioni locali assegnati da Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) nel sito Web MSDN.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Errore viene visualizzato quando un progetto flusso di lavoro viene distribuito in un sistema pulito  
 Questo problema si verifica se si distribuisce un progetto flusso di lavoro in un computer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con un sistema pulito. Un sistema pulito è un computer in cui è presente una nuova installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di SharePoint, ma non sono presenti progetti flusso di lavoro distribuiti.  
  
### <a name="error-message"></a>Messaggio di errore  
 Impossibile trovare l'elenco di SharePoint: cronologia del flusso di lavoro.  
  
### <a name="resolution"></a>Risoluzione  
 Questo errore si verifica a causa di un elenco di cronologia del flusso di lavoro mancano. Poiché l'ambiente di sviluppo è un sistema pulito, nessun flusso di lavoro viene distribuiti e l'elenco della cronologia del flusso di lavoro non esiste ancora. Per risolvere questo problema, riaprire la procedura guidata del flusso di lavoro, che determina l'elenco di cronologia del flusso di lavoro da creare.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Per immettere nuovamente la procedura guidata del flusso di lavoro  
  
1.  In **Esplora**, scegliere il nodo del flusso di lavoro.  
  
2.  Nel **proprietà** finestra, fare clic sul pulsante con puntini di sospensione (...) a una proprietà che contiene un pulsante con i puntini di sospensione.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>L'utente deve aggiornare la pagina applicazione nel Browser durante il debug per visualizzare l'immagine aggiornata  
 Se si esegue il debug di una soluzione di SharePoint che contiene una pagina dell'applicazione con un controllo che visualizza un'immagine, ad esempio un [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] controllo immagine, è necessario aggiornare la pagina nel browser per visualizzare le modifiche apportate all'immagine.  
  
## <a name="error-the-site-location-is-not-valid"></a>Errore: Il percorso del sito non è valido  
 Questo problema può verificarsi se [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] non è installato. Si potrebbe verificare anche se non si dispone dell'accesso come amministratore per il sito Web di SharePoint specificato nella **Personalizzazione guidata SharePoint**.  
  
### <a name="error-message"></a>Messaggio di errore  
  
-   Percorso del sito di SharePoint non è valido.  
  
### <a name="resolution"></a>Risoluzione  
  
-   Installare [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Verificare di disporre di accesso di amministratore per il sito Web di SharePoint. Per ulteriori informazioni, vedere il [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] articolo Online [concedere l'accesso al sito del portale](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Evento Web l'eliminazione del sito non è disponibile nel progetto ricevitore di eventi  
 Quando si crea un progetto di ricevitore di eventi e si selezionano determinati eventi Web, ad esempio "un sito di eliminazione in corso", l'evento si verifica mai.  
  
### <a name="error-message"></a>Messaggio di errore  
 Nessuno.  
  
### <a name="resolution"></a>Risoluzione  
 Questo problema si verifica perché l'ambito della funzionalità deve essere "Sito" per gestire gli eventi a livello di sito, ma l'ambito della funzionalità predefinita per i progetti di ricevitore di eventi è "Web". Gli eventi Web interessati sono:  
  
-   Un sito viene eliminato (WebDeleting)  
  
-   È stato eliminato un sito (WebDeleted)  
  
-   Un sito viene spostato (WebMoving)  
  
-   È stato spostato un sito (WebMoved)  
  
 Per risolvere il problema, modificare l'ambito della funzionalità del ricevitore di eventi, come indicato di seguito.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Per modificare l'ambito della funzionalità del ricevitore di eventi  
  
1.  In **Esplora**, aprire il file con estensione feature del ricevitore di eventi nel **Progettazione funzionalità** facendo doppio clic sul file o aprendo il menu di scelta rapida e scegliendo **aprire**.  
  
2.  Scegliere la freccia accanto a **ambito**, quindi scegliere **sito** nell'elenco visualizzato.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Errore di distribuzione viene visualizzato dopo avere modificato il nome di un identificatore in un progetto di modello connettività dati Business  
 Questo problema si verifica se si modifica il nome dell'identificatore di un'entità in un modello di integrazione applicativa dei dati (BDC) e quindi provare a distribuire la soluzione.  
  
### <a name="error-messages"></a>Messaggi di errore  
  
-   \<*nome del modello*> contiene gli errori di attivazione di tipo di contenuto esterno seguenti...  
  
-   IMetadataObject denominato '\<*nome modello*>' ha un valore nel campo 'name' che è duplicato...  
  
### <a name="resolution"></a>Risoluzione  
 Per risolvere questo problema, eliminare manualmente il modello e quindi distribuire nuovamente la soluzione.  È possibile eliminare il modello utilizzando uno degli strumenti seguenti:  
  
-   Amministrazione centrale SharePoint 2010. Per ulteriori informazioni, vedere [gestione del modello di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=181472) nel sito Web Microsoft TechNet.  
  
-   Windows PowerShell. È possibile eliminare il modello digitando questo comando al prompt dei comandi: **Remove-SPBusinessDataCatalogModel**. Per ulteriori informazioni, vedere [cmdlet generali (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) nel sito Web Microsoft TechNet.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Viene visualizzato un errore quando si tenta di visualizzare una Web Part visiva in SharePoint  
 Questo problema si verifica quando il **percorso** proprietà del controllo utente non inizia con la stringa "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Messaggi di errore  
  
-   Il file ' /_CONTROLTEMPLATES/*\<nome progetto >*/*\<nome della Web Part >*/*\<controllo utente nome >*ascx ' non esiste.  
  
-   Errore del server nell'applicazione '/'.  
  
### <a name="resolution"></a>Risoluzione  
  
##### <a name="to-resolve-this-issue"></a>Per risolvere il problema  
  
1.  In **Esplora**, scegliere il file di controllo utente, la cui estensione di file è ascx.  
  
2.  Nella barra dei menu, scegliere **vista**, **finestra proprietà**.  
  
3.  Nel **proprietà** finestra, espandere il **percorso di distribuzione** nodo.  
  
4.  Assicurarsi che il valore della **percorso** proprietà inizia con la stringa "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Errore durante l'esecuzione di un flusso di lavoro riutilizzabile importato contenente un campo del Form attività  
 Questo problema si verifica se si importa un flusso di lavoro che contiene un modulo di attività che dispone di un campo e quindi eseguirla di nuovo flusso di lavoro nello stesso sistema da cui è stato importato.  
  
### <a name="error-message"></a>Messaggio di errore  
 Errore durante il passaggio di distribuzione 'Attiva funzionalità': il campo con Id [*Guid*] definito nella funzionalità [*Guid*] è stato trovato nella raccolta siti corrente o in un sito secondario.  
  
### <a name="resolution"></a>Risoluzione  
 Questo errore è il risultato di conflitti di ID di campo che si verificano perché il flusso di lavoro riutilizzabile nel progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non modifica l'ID di campo modulo attività. Se si distribuisce un flusso di lavoro importato nello stesso server che contiene il flusso di lavoro originale, si verificano conflitti di campo ID.  
  
 Per risolvere questo problema, utilizzare la funzionalità Trova e Sostituisci per modificare il valore dell'attributo ID campo in tutti i file di flusso di lavoro importato.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Errore viene visualizzato quando importata rinominata viene eseguita l'istanza di elenco  
 Questo problema si verifica se si rinomina un'istanza di elenco importata e quindi eseguirlo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Messaggio di errore  
 Errore di compilazione: si è verificato un errore in fase di distribuzione 'Attiva funzionalità': il file Template\Features\\[*importare il progetto**funzionalità**nome*] \Files\Lists\\[*vecchio * * nome dell'elenco*] \Schema.xml non esiste.  
  
### <a name="resolution"></a>Risoluzione  
 Quando si importa un'istanza di elenco, un attributo denominato CustomSchema viene aggiunto al file Elements.xml dell'istanza di elenco. Elements include il percorso di un schema personalizzato per l'istanza di elenco. Quando si rinomina l'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cambia il percorso di distribuzione per il schema.xml personalizzato, ma il valore del percorso dell'attributo CustomSchema non viene aggiornato. Di conseguenza, l'istanza di elenco Impossibile trovare il file di schema nel percorso specificato dall'attributo CustomSchema quando viene attivata la funzionalità precedente.  
  
 Per risolvere questo problema, aggiornare il percorso di distribuzione del file di schema nell'attributo CustomSchema.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Sessione terminata da IIS di debug di SharePoint  
 Questo problema si verifica se si imposta un punto di interruzione un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] soluzione SharePoint, premere il tasto F5 per eseguire e quindi rimarrà in un punto di interruzione più di 90 secondi.  
  
### <a name="error-message"></a>Messaggio di errore  
 Processo del server Web a cui è stato eseguito il debug è stato terminato da Internet Information Services (IIS). Il problema può essere risolto configurando le impostazioni ping del pool di applicazioni in IIS. Vedere la Guida per ulteriori informazioni.  
  
### <a name="resolution"></a>Risoluzione  
 Per impostazione predefinita, il pool di applicazioni IIS attende 90 secondi per un'applicazione di rispondere prima della chiusura dell'applicazione. Questo processo è noto come "ping", l'applicazione. Per risolvere questo problema, è possibile aumentare il tempo di attesa o disabilitare completamente il ping di applicazione.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Per accedere alle impostazioni di pool di applicazioni IIS  
  
1.  Aprire Gestione IIS.  
  
2.  Nel **connessioni** riquadro espandere il nodo del server SharePoint e quindi scegliere il **pool di applicazioni** nodo.  
  
3.  Nel **pool di applicazioni** , selezionare il pool di applicazioni di SharePoint (in genere "SharePoint - 80"), quindi il **azioni** riquadro, scegliere il **impostazioni avanzate** collegamento.  
  
4.  Per aumentare il tempo di attesa prima del timeout IIS, modificare il valore di **il tempo di risposta massimo Ping (secondi)** su un valore maggiore di 90 secondi.  
  
5.  Per disabilitare il ping di IIS, impostare **Ping abilitato** a **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Istanza di elenco orfana lascia ritrazione automatica in SharePoint  
 Questo problema si verifica se vengono eseguiti i passaggi seguenti.  
  
1.  Creare una definizione di elenco che include un'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Premere il tasto F5 per eseguire la soluzione.  
  
3.  Interrompere il debug o chiudere il sito di SharePoint.  
  
4.  Riaprire il sito di SharePoint e aprire l'istanza di elenco.  
  
### <a name="error-message"></a>Messaggio di errore  
 Errore del server nell'applicazione '/'.  
  
### <a name="resolution"></a>Risoluzione  
 Ciò accade perché dopo la chiusura di una sessione di debug di una soluzione di SharePoint, la ritrazione automatica funzionalità ritrae la soluzione. Il ritiro Elimina la definizione di elenco da SharePoint, ma non l'istanza dell'elenco. La definizione di elenco sottostante è obbligatoria per l'istanza di elenco.  
  
 Per risolvere questo problema, distribuire la soluzione, nella barra dei menu, scegliendo **compilare**, **Distribuisci**. Non eseguire il debug della soluzione premendo il tasto F5. Eliminare quindi l'istanza di elenco in SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Soluzione di SharePoint originale viene sostituita da una versione esportata  
 Se si esporta una soluzione di SharePoint, Importa la soluzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e quindi distribuire la soluzione al sito stesso da cui è stato esportato, la soluzione SharePoint originale viene sostituita. Questo problema si verifica se si distribuisce la soluzione in un server che non dispone di una soluzione originale attivata su di esso.  
  
### <a name="error-message"></a>Messaggio di errore  
 Nessuno.  
  
### <a name="resolution"></a>Risoluzione  
 Per evitare la sovrascrittura di una soluzione nel sito da cui è stato esportato, modificare il GUID dell'IDSoluzione e gli ID di funzionalità di tutte le funzionalità importate nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto.  
  
## <a name="error-appears-when-debugging-starts"></a>Errore in caso di avvio del debug  
 Quando si avvia il debug di una soluzione SharePoint in Visual Studio, viene visualizzato un errore indicante che è impossibile caricare il file di configurazione Web.config in Visual Studio perché la chiave specificata non è presente nel dizionario.  
  
### <a name="error-message"></a>Messaggio di errore  
 Impossibile caricare il file di configurazione Web. config. Controllare il file per tutti gli elementi XML non valido e riprovare. Si è verificato l'errore seguente: la chiave specificata non è presente nel dizionario.  
  
### <a name="resolution"></a>Risoluzione  
 Per risolvere questo problema, verificare che il valore della proprietà URL sito del progetto SharePoint in Visual Studio corrisponda all'URL assegnato all'area predefinita per i mapping di accesso alternativo dell'applicazione Web. L'utilizzo di un'altra area, ad esempio Intranet, per l'URL non risolverà l'errore. L'URL del sito del progetto e l'URL nell'area predefinita devono corrispondere. Per accedere ai mapping di accesso alternativo, aprire l'utilità di amministrazione centrale SharePoint 2010, scegliere il **Application Management** collegamento, quindi in **applicazioni Web**, scegliere il  **Configurare i mapping di accesso alternativo** collegamento. Per ulteriori informazioni, vedere [creare zone per le applicazioni Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione e risoluzione dei problemi dei pacchetti di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Debug in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
