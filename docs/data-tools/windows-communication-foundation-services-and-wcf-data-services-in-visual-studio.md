---
title: Servizi Windows Communication Foundation e WCF Data Services in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 898cdbd15367aef6ac48d35a44b1ccb4a3deded9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servizi Windows Communication Foundation e dati WCF in Visual Studio
Visual Studio fornisce strumenti per l'utilizzo con Windows Communication Foundation (WCF) e [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], le tecnologie Microsoft per la creazione di applicazioni distribuite. In questo argomento viene fornita un'introduzione ai servizi da un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prospettiva. Per la documentazione completa, vedere [WCF Data Services 4.5](/dotnet/framework/data/wcf/index).  
  
## <a name="what-is-wcf"></a>Che cos'è WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]è un framework unificato per la creazione di applicazioni distribuite protette, affidabile, transazioni e interoperative. Sostituisce le tecnologie di comunicazione interprocesso precedente, ad esempio servizi Web ASMX, servizi remoti .NET, Enterprise Services (DCOM) e MSMQ. WCF unisce le funzionalità di tutte queste tecnologie in un modello di programmazione unificato. Ciò semplifica l'esperienza di sviluppo di applicazioni distribuite.  
  
#### <a name="what-are-wcf-data-services"></a>Quali sono i servizi dati WCF  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]è un'implementazione del protocollo OData (Open Data) standard.  WCF Data Services consente di esporre i dati tabulari come un set di API REST, che consente di restituire dati utilizzando i verbi HTTP standard quali GET, POST, PUT o DELETE. Sul lato server, WCF Data Services sono verranno sostituite da [ASP.NET Web API](http://www.asp.net/web-api) per la creazione di nuovi servizi OData. La libreria client WCF Data Services continua a essere una buona scelta per l'utilizzo dei servizi OData in un'applicazione .NET da Visual Studio (**progetto &#124; Aggiungi riferimento al servizio**). Per ulteriori informazioni, vedere [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### <a name="wcf-programming-model"></a>Modello di programmazione WCF  
 Il modello di programmazione WCF si basa sulla comunicazione tra due entità: un servizio WCF e un client WCF. Il modello di programmazione è incapsulato nel <xref:System.ServiceModel> spazio dei nomi di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### <a name="wcf-service"></a>Servizio WCF  
 Un servizio WCF è basato su un'interfaccia che definisce un contratto tra il servizio e il client. È contrassegnato con un <xref:System.ServiceModel.ServiceContractAttribute> attributo, come illustrato nel codice seguente:  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Si definiscono le funzioni o metodi esposti da un servizio WCF contrassegnandoli con un <xref:System.ServiceModel.OperationContractAttribute> attributo. Inoltre, è possibile esporre i dati serializzati per contrassegnare un tipo composito con un <xref:System.Runtime.Serialization.DataContractAttribute> attributo. Ciò consente l'associazione di dati in un client.  
  
 Dopo aver definiti un'interfaccia e i relativi metodi, vengono incapsulati in una classe che implementa l'interfaccia. Una singola classe di servizio WCF può implementare più contratti di servizio.  
  
 Un servizio WCF verrà esposti per l'utilizzo tramite è noto come un *endpoint*. L'endpoint fornisce l'unico modo per comunicare con il servizio. è possibile accedere al servizio tramite un riferimento diretto come si farebbe con altre classi.  
  
 Un endpoint è costituito da un indirizzo, un'associazione e un contratto. L'indirizzo definisce il servizio in cui si trova; potrebbe trattarsi di un URL, un indirizzo FTP, o una rete o un percorso locale. Un'associazione definisce la modalità di comunicazione con il servizio. Le associazioni WCF forniscono un modello versatile per specificare un protocollo, ad esempio HTTP o FTP, un meccanismo di sicurezza, ad esempio l'autenticazione di Windows o nomi utente e password e molto altro ancora. Un contratto include le operazioni esposte dalla classe del servizio WCF.  
  
 È possibile esporre più endpoint per un singolo servizio WCF. In questo modo i client diversi comunicare con lo stesso servizio in modi diversi. Ad esempio, un servizio di servizi bancari potrebbe fornire un endpoint per i dipendenti e un altro per i clienti esterni, ognuno dei quali utilizza un indirizzo diverso, l'associazione e/o del contratto.  
  
#### <a name="wcf-client"></a>Client di WCF  
 Un client WCF è costituito da un *proxy* che consente a un'applicazione comunicare con un servizio WCF e un endpoint che corrisponde a un endpoint definito per il servizio. Il proxy viene generato sul lato client nel file app. config e include informazioni sui tipi e metodi esposti dal servizio. Per i servizi che espongono più endpoint, il client può selezionare quella più adatta alle esigenze, ad esempio, per comunicare tramite HTTP e utilizzare l'autenticazione di Windows.  
  
 Dopo aver creato un client WCF, si fa riferimento il servizio nel codice come qualsiasi altro oggetto. Ad esempio, per chiamare il `GetData` metodo illustrato in precedenza, è necessario scrivere codice simile al seguente:  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Strumenti WCF in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]fornisce strumenti che consentono di creare servizi WCF e client WCF. Per una procedura dettagliata che illustra gli strumenti, vedere [procedura dettagliata: creazione di un semplice servizio WCF in Windows Form](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### <a name="creating-and-testing-wcf-services"></a>Creare e testare i servizi WCF  
 È possibile utilizzare WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelli come base per creare rapidamente un servizio specifico. È quindi possibile utilizzare Host automatico servizio di WCF e Client di prova WCF per eseguire il debug e testare il servizio. Insieme, questi strumenti forniscono un rapido e comodo debug e test ed eliminano la necessità di eseguire il commit di un modello di hosting in fase iniziale.  
  
#### <a name="wcf-templates"></a>Modelli di WCF  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelli forniscono una struttura di classe base per lo sviluppo del servizio. Sono disponibili in vari modelli WCF di **Aggiungi nuovo progetto** la finestra di dialogo. Tra i progetti libreria di servizi WCF, siti Web dei servizi WCF e modelli di elemento di servizio WCF.  
  
 Quando si seleziona un modello, i file vengono aggiunti per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio. Tutti gli attributi necessari sono già presenti, la creazione di un tipo semplice "Hello World" del servizio, e non è stato necessario scrivere codice. Naturalmente, verrà, si desidera aggiungere il codice per fornire funzioni e metodi per il servizio del mondo reale, ma i modelli forniscono la base.  
  
 Per ulteriori informazioni sui modelli WCF, vedere [modelli di Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).  
  
#### <a name="wcf-service-host"></a>Host servizio WCF  
 Quando si avvia il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del debugger (premendo F5) per un progetto di servizio WCF, l'Host del servizio WCF strumento viene avviato automaticamente per ospitare il servizio localmente. Host servizio WCF enumera i servizi in un progetto di servizio WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio che trova.  
  
 Mediante Host servizio WCF, è possibile testare un servizio WCF senza scrivere codice aggiuntivo o eseguire il commit di un host specifico durante lo sviluppo.  
  
 Per ulteriori informazioni sull'Host servizio WCF, vedere [Host servizio WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).  
  
#### <a name="wcf-test-client"></a>Client di prova WCF  
 Lo strumento Client di prova WCF consente di immettere parametri di test, inviare l'input a un servizio WCF e visualizzare la risposta restituita dal servizio. Fornisce un semplice test quando si combinarla con Host servizio WCF del servizio. Lo strumento è reperibile nella cartella \Common7\IDE, ovvero per Visual Studio 2015 installati nell'unità c: di seguito: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.  
  
 Quando si preme F5 per eseguire il debug di un progetto di servizio WCF, il Client di prova WCF aprirà e visualizzerà un elenco di endpoint del servizio che sono definiti nel file di configurazione. È possibile verificare i parametri di avviare il servizio e ripetere questa procedura per testare e convalidare il servizio continuamente.  
  
 Per ulteriori informazioni sui Client di prova WCF, vedere [Client di prova WCF (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>L'accesso ai servizi WCF in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]semplifica l'attività di creazione di client WCF, la generazione automatica di un proxy e un endpoint per servizi aggiunti tramite il **Aggiungi riferimento al servizio** la finestra di dialogo. Tutte le informazioni di configurazione necessarie viene aggiunto al file app. config. La maggior parte dei casi, è necessario creare un'istanza del servizio per poter essere utilizzato.  
  
 Il **Aggiungi riferimento al servizio** la finestra di dialogo consente di immettere l'indirizzo per un servizio o per cercare un servizio che viene definito nella soluzione. Nella finestra di dialogo restituisce un elenco di servizi e le operazioni fornite da tali servizi. Consente inoltre di definire lo spazio dei nomi da cui si farà riferimento ai servizi nel codice.  
  
 Il **Configura riferimento a servizio** la finestra di dialogo consente di personalizzare la configurazione di un servizio. È possibile modificare l'indirizzo per un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto messaggio e configurare riutilizzo dei tipi.  
  
## <a name="how-to-select-a-service-endpoint"></a>Procedura: selezionare un Endpoint del servizio  
Alcuni servizi Windows Communication Foundation (WCF) espongono più endpoint tramite il quale un client può comunicare con il servizio. Ad esempio, un servizio può esporre un endpoint che utilizza un nome utente e l'associazione di HTTP / protezione password e un secondo endpoint che utilizza FTP e l'autenticazione di Windows. Il primo endpoint potrebbe essere utilizzato da applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere utilizzato in una rete intranet.  
  
In tal caso, è possibile specificare il `endpointConfigurationName` come parametro al costruttore per un riferimento al servizio.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>Per selezionare un endpoint del servizio  
  
1.  Aggiungere un riferimento a un servizio WCF facendo clic sul nodo del progetto in Esplora soluzioni e scegliendo **Aggiungi riferimento al servizio**.
  
2.  Nell'Editor di codice, aggiungere un costruttore per il riferimento al servizio:  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Sostituire *ServiceReference* con lo spazio dei nomi di riferimento al servizio e sostituire *Service1Client* con il nome del servizio.  
  
3.  Verrà visualizzato un elenco di IntelliSense con gli overload del costruttore. Selezionare il `endpointConfigurationName As String` rapporto di overload.  
  
4.  Dopo l'overload, digitare `=` *ConfigurationName*, dove *ConfigurationName* è il nome dell'endpoint che si desidera utilizzare.  
  
    > [!NOTE]
    >  Se non si conoscono i nomi degli endpoint disponibili, è possibile trovarli nel file app. config.  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Per trovare gli endpoint disponibili per un servizio WCF  
  
1.  In **Esplora**, il file app. config per il progetto che contiene il riferimento al servizio e quindi fare clic su **aprire**. Il file verrà visualizzato nell'Editor di codice.  
  
2.  Cercare il `<Client>` tag nel file.  
  
3.  Cercare di sotto di `<Client>` tag per un tag che inizia con `<Endpoint>`.  
  
     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più `<Endpoint` tag.  
  
4.  All'interno di `<EndPoint>` tag troverà un `name="` *nomeservizio* `"` parametro (in cui *nomeservizio* rappresenta un nome di endpoint). Si tratta del nome per l'endpoint che può essere passato al `endpointConfigurationName As String` overload di un costruttore per un riferimento al servizio.  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>Procedura: chiamare un metodo del servizio in modo asincrono  
La maggior parte dei metodi in servizi di Windows Communication Foundation (WCF) possono essere chiamati in modo sincrono o asincrono. Chiamata a un metodo in modo asincrono consente all'applicazione di continuare a lavorare durante il metodo viene chiamato quando opera su una connessione lenta.  
  
Per impostazione predefinita, quando viene aggiunto un riferimento al servizio a un progetto è configurato per chiamare i metodi in modo sincrono. È possibile modificare il comportamento per chiamare i metodi modificando un'impostazione in modo asincrono il **Configura riferimento a servizio** la finestra di dialogo.  
  
> [!NOTE]
>  Questa opzione è impostata in base al servizio. Se un metodo per un servizio viene chiamato in modo asincrono, tutti i metodi devono essere chiamati in modo asincrono.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>Per chiamare un metodo di servizio in modo asincrono  
  
1.  In **Esplora**, selezionare il riferimento al servizio.  
  
2.  Nel **progetto** menu, fare clic su **Configura riferimento a servizio**.  
  
3.  Nel **Configura riferimento a servizio** la finestra di dialogo, seleziona il **Genera operazioni asincrone** casella di controllo.  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>Procedura: associare dati restituiti da un servizio  
È possibile associare dati restituiti da un servizio Windows Communication Foundation (WCF) a un controllo come qualsiasi altra origine dati è possibile associare a un controllo. Quando si aggiunge un riferimento a un servizio WCF, se il servizio contiene tipi compositi che restituiscono dati, vengono aggiunti automaticamente per il **origini dati** finestra.  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Per associare un controllo a singolo campo di dati restituito da un servizio WCF  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**. Il **origini dati** verrà visualizzata la finestra.  
  
2.  Nel **origini dati** finestra, espandere il nodo del riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Espandere un nodo per un tipo. I campi dati per tale tipo verranno visualizzati.  
  
4.  Selezionare un campo e fare clic sulla freccia a discesa per visualizzare un elenco di controlli che sono disponibili per il tipo di dati.  
  
5.  Fare clic sul tipo di controllo che si desidera associare.  
  
6.  Trascinare il campo in un form. Il controllo verrà aggiunto al form insieme a un <xref:System.Windows.Forms.BindingSource> componente e un <xref:System.Windows.Forms.BindingNavigator> componente.  
  
7.  Ripetere i passaggi da 4 a 6 per eventuali altri campi che si desidera associare.  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Per associare un controllo composito tipo restituito da un servizio WCF  
  
1.  Nel **dati** dal menu **Mostra origini dati**. Il **origini dati** verrà visualizzata la finestra.  
  
2.  Nel **origini dati** finestra, espandere il nodo del riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Selezionare un nodo per un tipo e fare clic sulla freccia a discesa per visualizzare un elenco delle opzioni disponibili.  
  
4.  Fare clic su **DataGridView** per visualizzare i dati in una griglia o **dettagli** per visualizzare i dati in singoli controlli.  
  
5.  Trascinare il nodo nel form. Verranno aggiunti i controlli al form insieme a un <xref:System.Windows.Forms.BindingSource> componente e un <xref:System.Windows.Forms.BindingNavigator> componente.  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedura: configurare un servizio per riutilizzare i tipi esistenti  
Quando un riferimento al servizio viene aggiunto a un progetto, i tipi definiti nel servizio vengono generati nel progetto locale. In molti casi, ciò crea tipi duplicati quando un servizio utilizza comuni [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipi o quando i tipi sono definiti in una libreria condivisa.  
  
Per evitare questo problema, i tipi negli assembly di riferimento vengono condivisi per impostazione predefinita. Se si desidera disabilitare la condivisione di tipi per uno o più assembly, è possibile eseguire questa operazione nel **Configura riferimento a servizio** la finestra di dialogo.  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Per disabilitare la condivisione in un singolo assembly dei tipi  
  
1.  In **Esplora**, selezionare il riferimento al servizio.  
  
2.  Nel **progetto** menu, fare clic su **Configura riferimento a servizio**.  
  
3.  Nel **Configura riferimento a servizio** nella finestra di dialogo **Riutilizza tipi negli assembly di riferimento specificati**.  
  
4.  Selezionare la casella di controllo per ogni assembly in cui si desidera abilitare la condivisione dei tipi. Per disabilitare la condivisione di tipi per un assembly, lasciare deselezionata la casella di controllo.  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Per disabilitare la condivisione in tutti gli assembly di tipo  
  
1.  In **Esplora**, selezionare il riferimento al servizio.  
  
2.  Nel **progetto** menu, fare clic su **Configura riferimento a servizio**.  
  
3.  Nel **Configura riferimento a servizio** la finestra di dialogo, deseleziona il **Riutilizza tipi negli assembly di riferimento** casella di controllo.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creazione di un Windows Form semplice](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Fornisce informazioni dettagliate sulla creazione e utilizzo dei servizi WCF in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Procedura dettagliata: creazione di un servizio dati WCF con WPF ed Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Fornisce una spiegazione dettagliata su come creare e utilizzare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Uso degli strumenti di sviluppo WCF](/dotnet/framework/wcf/using-the-wcf-development-tools)|Viene descritto come creare e testare i servizi WCF in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
||[Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Viene illustrato come utilizzare e fare riferimento [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md)|Presenta alcuni errori comuni che possono verificarsi con riferimenti a servizi e come evitarli.|  
|[Debug dei servizi WCF](../debugger/debugging-wcf-services.md)|Descrive i problemi di debug comuni e le tecniche che possono verificarsi durante il debug dei servizi WCF.|  
|[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti.|  
|[Configura riferimento a servizio (finestra di dialogo)](../data-tools/configure-service-reference-dialog-box.md)|Vengono descritti gli elementi dell'interfaccia utente di **Configura riferimento a servizio** la finestra di dialogo.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)