---
title: Progettazione di un modello di integrazione applicativa dei dati Business | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f34a754562674aacf989c294ff2662ca4f8f28f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="designing-a-business-data-connectivity-model"></a>Progettazione di un modello di integrazione applicativa dei dati
  È possibile sviluppare un modello per il servizio di integrazione applicativa dei dati (BDC) mediante l'aggiunta di metodi e le entità in un file di modello. Un'entità descrive una raccolta di campi dati. Ad esempio, un'entità può rappresentare una tabella in un database. Un metodo esegue un'attività, ad esempio aggiunta, eliminazione o aggiornamento dei dati rappresentati dalle entità. Per ulteriori informazioni, vedere [l'integrazione di dati di Business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="adding-entities"></a>Aggiunta di entità  
 È possibile aggiungere un'entità trascinando o copiando un **entità** da Visual Studio **della casella degli strumenti** nella finestra di progettazione di integrazione applicativa dei dati. Per ulteriori informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definire i campi dell'entità in una classe. Ad esempio, è possibile aggiungere un campo denominato `Address` per un `Customer` classe. È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata utilizzando altri strumenti, ad esempio il Object Relational Designer (O/R Designer). Il nome dell'entità e il nome della classe che rappresenta l'entità non devono corrispondere. La classe viene correlata all'entità quando si definiscono i metodi nel modello.  
  
## <a name="adding-methods"></a>Aggiunta di metodi  
 Il servizio di integrazione applicativa dei dati chiama i metodi nel modello quando gli utenti di visualizzano, aggiungere, aggiornare o eliminare le informazioni in un elenco o una Web Part che è basato sul modello. È necessario aggiungere un metodo per il modello per ogni attività che l'utente può eseguire. Creare metodi selezionando uno dei cinque tipi di metodo di base dal **Dettagli metodo di integrazione applicativa dei dati** finestra. Nella tabella seguente vengono descritti i cinque metodi di base di un modello di integrazione applicativa dei dati.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Finder|Restituisce una raccolta di istanze di entità. Chiamato quando l'utente apre l'elenco o una Web Part. Per ulteriori informazioni, vedere [procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md).|  
|Finder specifico|Restituisce un'istanza di entità specifico. Chiamato quando un utente visualizza i dettagli di un elemento specifico in un elenco. Per ulteriori informazioni, vedere [procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Aggiunge nuovi dati all'origine dati di un'entità. Chiamato quando gli utenti scelgono di **nuovo elemento** pulsante della barra multifunzione di un elenco che è basato sul modello. Per ulteriori informazioni, vedere [procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modifica i dati in un elenco. Chiamato quando gli utenti aggiornano le informazioni in un elenco. Per ulteriori informazioni, vedere [procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Rimuove i dati. Chiamato quando gli utenti di eliminare un elemento dall'elenco. Per ulteriori informazioni, vedere [procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="defining-method-parameters"></a>Definizione dei parametri di metodo  
 Quando si crea un metodo, Visual Studio aggiunge i parametri di input e outpui appropriati per il tipo di metodo. Questi parametri sono semplicemente segnaposto. Nella maggior parte dei casi, è necessario modificare i parametri in modo che possano passare o restituire il tipo di dati corretto. Ad esempio, per impostazione predefinita, un metodo Finder restituisce una stringa. Nella maggior parte dei casi, si desidera modificare il parametro restituito del metodo Finder in modo che restituisca una raccolta di entità. È possibile eseguire tale operazione modifica il descrittore di tipo del parametro. Un descrittore di tipo è una raccolta di attributi che descrive il tipo di dati di un parametro. Per ulteriori informazioni, vedere [procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio consente di copiare i descrittori di tipo tra i parametri del modello. Ad esempio, è possibile definire un descrittore di tipo denominato `CustomerTD` per il parametro restituito di `GetCustomer` metodo. È possibile copiare il `CustomerTD` digitare descrittore nel **Esplora integrazione applicativa dei dati**e quindi incollare il descrittore di tipo per il parametro di input di `CreateCustomer` (metodo). Ciò impedisce all'utente di dover definire più di una volta il descrittore di tipo stesso.  
  
##  <a name="MethodInstances"></a> Istanze (metodo)  
 Quando si crea un metodo, Visual Studio aggiunge un'istanza predefinita del metodo. Un'istanza del metodo è un riferimento a un metodo, più i valori predefiniti per i parametri. Un singolo metodo può avere più istanze di metodo. Ogni istanza è una combinazione di firma del metodo e un set di valori predefiniti. Per ulteriori informazioni, vedere [procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Quando si esegue il progetto, vengono visualizzate le istanze di metodo in un elenco a discesa sopra l'elenco di SharePoint. Gli utenti possono scegliere istanze del metodo per visualizzare i dati.  
  
 Per aggiungere i valori predefiniti per l'istanza del metodo, è necessario modificare direttamente il codice XML del modello. Per ulteriori informazioni, vedere [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="adding-filter-descriptors"></a>Aggiunta di descrittori di filtro  
 I consumer del modello potrebbe essere necessario recuperare le istanze di un'entità che corrispondono a certi criteri. Per abilitare questa funzionalità, è possibile aggiungere un descrittore di filtro a un metodo. Descrittori di filtro consentono ai consumer del modello filtrare il set di risultati di metodo per passare valori a metodi prima che vengano eseguiti. Per ulteriori informazioni, vedere [procedura: aggiungere parametri di filtro per le operazioni per limitare le istanze del sistema esterno](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint fornisce diverse funzionalità che consentono agli utenti di fornire i valori di filtro. Web part dei dati di Business forniscono, ad esempio, una casella di testo del filtro. Gli utenti possono limitare i dati in un elenco immettendo un valore nella casella di testo. Per ulteriori informazioni su come aggiungere un descrittore di filtro a un metodo, vedere [procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Proprietà del descrittore di filtro  
 È necessario impostare il valore di **associata descrittore di tipo**, **nome**, e **tipo** proprietà di un descrittore di filtro. Tutte le altre proprietà sono facoltativi.  
  
 Il **associata descrittore di tipo** proprietà correlata il descrittore di filtro per un parametro di input. Quando un utente fornisce un valore di filtro, il servizio di integrazione applicativa dei dati passa tale valore nel metodo utilizzando il parametro di input.  
  
 Il **tipo** proprietà descrive il criterio di filtro che si desidera utilizzare. In SharePoint, il criterio di filtro selezionato determina il testo visualizzato nell'interfaccia utente (UI). Ad esempio, per un criterio di filtro di confronto, il testo **è uguale a** viene visualizzato come controllo di una Web Part dati Business. Per ulteriori informazioni su ogni criterio di filtro, vedere [tipi di filtri supportati per l'integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Per ulteriori informazioni sulle proprietà di un descrittore di filtro, vedere [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="providing-default-values"></a>Fornire i valori predefiniti  
 In alcuni casi, l'utente potrebbe non fornire un valore di filtro. È possibile fornire un valore predefinito tramite l'aggiunta di un valore predefinito per l'istanza del metodo oppure impostando il valore predefinito nel codice del metodo. Per ulteriori informazioni su come aggiungere un valore predefinito per l'istanza del metodo, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Per un esempio di come impostare il valore predefinito di un parametro di input nel codice del metodo, vedere [procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validating-the-model"></a>La convalida del modello  
 È possibile convalidare il modello durante lo sviluppo. Visual Studio identifica i problemi che possono impedire il modello di funzioni come previsto. Tali problemi vengono visualizzati in Visual Studio **elenco errori**.  
  
 È possibile convalidare un modello di aprire il menu di scelta rapida per la finestra di progettazione di integrazione applicativa dei dati e quindi scegliendo **convalida**. Se il modello contiene errori, vengono visualizzati nel **elenco errori**. È possibile spostare rapidamente il cursore sul codice contenente un errore facendo doppio clic sull'errore nell'elenco. In alternativa, è possibile scegliere ripetutamente i tasti F8 o MAIUSC+F8 per spostarsi avanti o indietro negli errori nell'elenco.  
  
 Quando le regole del modello vengono violate in qualche modo, possono verificarsi errori di convalida. Ad esempio, se il **IsCollection** di un descrittore di tipo è impostata su **true**, ma non descrittori di tipo figlio esistono, verrà visualizzato un errore di convalida. Potrebbe essere necessario fare riferimento alle regole di un modello di integrazione applicativa dei dati per comprendere alcuni errori visualizzati in Visual Studio **elenco errori**. Per ulteriori informazioni sulle regole di un modello di integrazione applicativa dei dati, vedere [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debugging-the-solution-that-contains-the-model"></a>Il debug della soluzione che contiene il modello  
 Come per qualsiasi codice in Visual Studio, è possibile eseguire il debug del codice. Per eseguire il debug del codice, impostare punti di interruzione in qualsiasi punto nel codice e quindi avviare il debugger. Visual Studio apre il sito di SharePoint. In SharePoint, creare un elenco o una Web Part che utilizza i dati aziendali. Quindi, è possibile esaminare il codice. Per ulteriori informazioni sul debug di progetti SharePoint, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 È anche possibile eseguire il debug di codice negli assembly personalizzati aggiunti al progetto. Tuttavia, per eseguire il debug di codice in un assembly personalizzato, è necessario aggiungere l'assembly per il pacchetto della soluzione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per ulteriori informazioni sull'aggiunta di un assembly personalizzato al progetto, vedere [procedura: includere un Assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configuring-bdc-security"></a>Configurazione della protezione di integrazione applicativa dei dati  
 Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint prima di poter eseguire il debug della soluzione. Per modificare queste impostazioni, aprire l'applicazione di servizio connettività dati Business nel sito Web di SharePoint 2010 centrale amministrazione. Nel **impostare autorizzazioni per l'archivio dei metadati** la finestra di dialogo, aggiungere l'account utente, quindi selezionare una qualsiasi delle opzioni seguenti:  
  
|Attività|Opzione|  
|----------|------------|  
|Per distribuire i modelli per il servizio di integrazione applicativa dei dati.|Edit|  
|Per creare elenchi e le Web part tramite esterno tipi di contenuto (entità) nel modello.|Selezione nei client|  
|Per creare, leggere, aggiornare ed eliminare dati di entità.|Esegui|  
  
 Per ulteriori informazioni su queste impostazioni, vedere [gestione dei servizi di integrazione applicativa dei dati Business](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 È inoltre possibile impostare le autorizzazioni di sicurezza per singoli modelli o tipi di contenuto esterno. Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un modello, vedere [gestione del modello di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=178884). Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un tipo di contenuto esterno, vedere [gestione dei tipi di contenuto esterno](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Utilizzare queste impostazioni per il debug di una soluzione nel SharePoint Server locale. Per ulteriori informazioni su come configurare le impostazioni di sicurezza correlati di integrazione applicativa dei dati nel server di produzione SharePoint, vedere [Cenni preliminari sulla sicurezza di servizi di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retracting-models-that-become-corrupt"></a>Ritrazione dei modelli danneggiati  
 Quando il debugger viene avviato per la prima volta, in Visual Studio l'intero modello viene distribuito in SharePoint. Per ogni periodo di tempo in seguito, Visual Studio aggiorna il modello in SharePoint con le eventuali modifiche apportate tra le distribuzioni.  
  
 Potrebbero esistere situazioni in cui si desidera che Visual Studio per ritrarre completamente il modello da SharePoint. Ad esempio, un modello potrebbe essere danneggiato.  Per ridistribuire il modello in SharePoint, impostare il **aggiornamento incrementale** proprietà del modello da **False**, e quindi avviare il debugger. Il **aggiornamento incrementale** proprietà viene visualizzata nel **proprietà** finestra quando si seleziona il nodo che rappresenta il modello nel **Esplora integrazione applicativa dei dati**. Per impostazione predefinita, il nome del modello è **BdcModel1**.  
  
### <a name="changing-identifier-names-of-entities-in-the-model"></a>Modifica i nomi degli identificatori di entità nel modello  
 Se si modifica il nome di un identificatore dopo avere distribuito il modello, si potrebbe ricevere un errore di distribuzione. Non è possibile risolvere l'errore impostando il **aggiornamento incrementale** proprietà del modello da **False**. È necessario recuperare manualmente il modello e quindi distribuire nuovamente la soluzione. Per ulteriori informazioni, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). È possibile evitare questo errore impostando il **aggiornamento incrementale** proprietà **False** prima di distribuire inizialmente il modello.  
  
## <a name="locating-documentation-for-bdc-model-elements"></a>Individuazione di documentazione per gli elementi del modello di integrazione applicativa dei dati  
 Visual Studio aggiunge un elemento XML al modello per ogni entità, metodo o un altro elemento che si crea. Attributi dell'elemento vengono visualizzate le proprietà nel **proprietà** finestra. Per informazioni sugli elementi e attributi generato da Visual Studio quando si progetta il modello, vedere [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)|Vengono descritti gli strumenti che è possibile utilizzare per progettare un modello per l'integrazione applicativa dei dati.|  
|[Procedura: Aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)|Viene illustrato come aggiungere tipi di contenuto esterno, o entità, al modello.|  
|[Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di visualizzare un elenco di entità in un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di visualizzare i dettagli di un'entità specifica.|  
|[Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di aggiungere record a un'origine dati direttamente da un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di rimuovere i dati da un'origine dati utilizzando le opzioni dell'interfaccia utente (UI) di un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di modificare i record di dati in un'origine dati direttamente da un elenco o una Web Part.|  
|[Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Viene illustrato come utilizzare la finestra Dettagli metodo in Visual Studio per aggiungere parametri di input e restituiti a un metodo.|  
|[Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Viene illustrato come definire i tipi di dati di parametro nel modello.|  
|[Procedura: Definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)|Viene illustrato come creare un'istanza di un metodo che esegue l'integrazione applicativa dei dati.|  
|[Procedura: Aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Viene illustrato come consentire agli utenti di limitare il numero di istanze restituite da un metodo Finder.|  
|[Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)|Viene descritto come definire le relazioni tra entità nel modello. Web part dei dati di business, gli elenchi esterni e applicazioni personalizzate possono visualizzare queste relazioni di dati in un'interfaccia utente (UI).|  
|[Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)|Viene illustrato come definire le relazioni tra entità nel modello.|  
|[Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Vengono fornite istruzioni dettagliate che illustrano come creare e testare un modello che consente di visualizzare i contatti in un elenco esterno di SharePoint.|  
|[Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Viene fornita una panoramica della creazione e la progettazione di modelli per il servizio di integrazione applicativa dei dati.|  
  
  