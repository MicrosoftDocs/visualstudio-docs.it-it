---
title: Debug delle soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1be963dec8eee77efe4855c2e810af0fd1e72f1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-sharepoint-solutions"></a>Debug di soluzioni SharePoint
  È possibile eseguire il debug di soluzioni SharePoint tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger. Quando si avvia il debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce i file di progetto nel server SharePoint e quindi viene aperta un'istanza del sito di SharePoint nel Web browser. Le sezioni seguenti illustrano come eseguire il debug di applicazioni di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Abilitazione del debug](#EnableDebug)  
  
-   [Processo di distribuzione e debug con F5](#Deployment)  
  
-   [Funzionalità del progetto SharePoint](#Features)  
  
-   [Esecuzione del debug dei flussi di lavoro](#Workflow)  
  
-   [Ricevitori di eventi di debug](#FeatureEvents)  
  
-   [L'abilitazione di informazioni di debug avanzate](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Abilitazione del debug  
 Durante il debug prima di una soluzione di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], una finestra di dialogo segnala che il file Web. config non è configurato per abilitare il debug. (Il file Web. config viene creato quando si installa SharePoint server. Per ulteriori informazioni, vedere [utilizzo dei file Web. config](http://go.microsoft.com/fwlink/?LinkID=149266).) Nella finestra di dialogo consente di scegliere se eseguire il progetto senza debug o la modifica del file Web. config per abilitare il debug. Se si sceglie la prima opzione, il progetto viene eseguito normalmente. Se si sceglie la seconda opzione, il file web.config viene configurato per:  
  
-   Attivare lo stack di chiamate (`CallStack="true"`)  
  
-   Disabilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
-   Abilitare il debug di compilazione (`<compilation debug="true">`)  
  
 Il file Web. config seguente:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 Per annullare le modifiche e disabilitare il debug, modificare gli elementi seguenti [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] nel file Web. config:  
  
-   Disattivare lo stack di chiamate (`CallStack="false"`)  
  
-   Abilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Disabilitare il debug di compilazione (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a> Processo di distribuzione e debug con F5  
 Quando si esegue il progetto SharePoint in modalità di debug, il processo di distribuzione di SharePoint vengono eseguite le attività seguenti:  
  
1.  Esegue i comandi pre-distribuzione personalizzabili.  
  
2.  Crea un file di pacchetto (con estensione wsp) soluzione Web tramite [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comandi. Il file con estensione wsp include tutti i file necessari e le funzionalità. Per ulteriori informazioni, vedere [Cenni preliminari sulle soluzioni](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Se la soluzione di SharePoint è una soluzione farm, viene riciclato il [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni per il sito specificato [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Questo passaggio rilascia file bloccati dal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo di lavoro.  
  
4.  Se esiste già una versione precedente del pacchetto, viene ritratta la versione precedente delle funzionalità e i file nel file con estensione wsp. Questo passaggio disattiva le funzionalità, disinstalla il pacchetto della soluzione e quindi Elimina il pacchetto della soluzione nel server SharePoint.  
  
5.  Installa la versione corrente dei file di funzionalità e nel file con estensione wsp. Questo passaggio aggiunge e installa la soluzione nel server SharePoint.  
  
6.  Per i flussi di lavoro, installa l'assembly del flusso di lavoro. È possibile modificare il percorso utilizzando il *il percorso dell'Assembly* proprietà.  
  
7.  Attiva la funzionalità del progetto SharePoint, se l'ambito è sito o Web. Funzionalità negli ambiti Farm e WebApplication non sono attivate.  
  
8.  Per i flussi di lavoro, associa il flusso di lavoro con la raccolta di SharePoint, elenco o sito selezionato nel **Personalizzazione guidata SharePoint**.  
  
    > [!NOTE]  
    >  Questa associazione si verifica solo se si seleziona **automaticamente associazione flusso di lavoro** nella procedura guidata.  
  
9. Esegue i comandi di post-distribuzione personalizzabili.  
  
10. Connette il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al processo [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (w3wp.exe). Se il tipo di progetto consente di modificare il *soluzione creata mediante sandbox* proprietà e il relativo valore è impostato su **true**, il debugger viene connesso a un altro processo (SPUCWorkerProcess.exe). Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Avvia il debugger JavaScript se la soluzione di SharePoint è una soluzione farm.  
  
12. Consente di visualizzare la libreria appropriata, un elenco o una pagina del sito nel Web browser.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di stato nella finestra di Output dopo ogni attività è stata completata. Se non è possibile completare un'attività, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di errore nella finestra Elenco errori.  
  
##  <a name="Features"></a> Funzionalità del progetto SharePoint  
 Una funzionalità è un'unità modulare e portatile di funzionalità che semplifica la modifica dei siti utilizzando le definizioni di sito. È anche un pacchetto di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementi (WSS) che può essere attivato per un ambito specifico e che consente agli utenti di eseguire un particolare obiettivo o un'attività. I modelli vengono distribuiti come funzioni.  
  
 Quando si esegue un progetto in modalità di debug, il processo di distribuzione crea una cartella di *funzionalità* directory in %COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES. I nomi delle funzionalità con il formato *nome progetto*feature*x*, ad esempio TestProject_Feature1.  
  
 La cartella della soluzione nella directory delle caratteristiche contiene un *definizione della caratteristica* file e un *definizione flusso di lavoro* file. Il file di definizione di funzionalità (feature) vengono descritti i file in indicato del progetto file di definizione del progetto (Elements) descrive il modello di progetto. Elements è reperibile **Esplora**, ma feature non viene generato quando viene creato il pacchetto della soluzione. Per ulteriori informazioni su questi file, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Debug dei flussi di lavoro  
 Quando si esegue il debug di progetti di flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il modello di flusso di lavoro (a seconda del tipo) a una raccolta o a un elenco. È quindi possibile avviare il modello di flusso di lavoro manualmente o mediante l'aggiunta o aggiornamento di un elemento. È quindi possibile utilizzare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per eseguire il debug del flusso di lavoro.  
  
> [!NOTE]  
>  Se si aggiungono riferimenti ad altri assembly, assicurarsi che tali assembly vengono installati nella global assembly cache ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). In caso contrario, la soluzione del flusso di lavoro avrà esito negativo. Per informazioni su come installare gli assembly, vedere [avviare manualmente un flusso di lavoro su un documento o un elemento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Tuttavia, il processo di distribuzione non viene avviato il flusso di lavoro. È necessario avviare il flusso di lavoro dal sito Web di SharePoint. È anche possibile avviare il flusso di lavoro tramite un'applicazione client, ad esempio Microsoft Office Word 2010 o tramite codice lato server separato. Utilizzare uno degli approcci specificati nella **Personalizzazione guidata SharePoint**.  
  
 Ad esempio, se si specifica che il flusso di lavoro possa essere avviato manualmente, è possibile avviare il flusso di lavoro direttamente dall'elemento della raccolta o un elenco. Per ulteriori informazioni su come avviare un flusso di lavoro manualmente, vedere [avviare manualmente un flusso di lavoro su un elemento del documento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Ricevitori di eventi di debug  
 Per impostazione predefinita, quando si esegue un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazione SharePoint, le funzionalità vengono attivate automaticamente per l'utente nel server SharePoint. Tuttavia, questa operazione causa problemi durante il debug di ricevitori di eventi perché quando una funzionalità viene attivata da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene eseguito in un processo diverso dal debugger. Ciò significa che alcune funzionalità di debug, ad esempio punti di interruzione, non funzionerà correttamente.  
  
 Per disabilitare l'attivazione automatica della funzionalità in SharePoint e consentire il debug corretto dei ricevitori di eventi di funzionalità, impostare la proprietà del progetto **configurazione distribuzione attiva** proprietà **Nessuna attivazione** prima del debug. Successivamente, dopo aver avviato il debug dell'applicazione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], attivare manualmente la funzionalità in SharePoint. Per attivare la funzionalità, aprire il **Azioni sito** menu in SharePoint, scegliere **Impostazioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento e quindi scegliere il **Attiva** pulsante accanto alla funzionalità e continuare il debug come di consueto.  
  
##  <a name="EnhancedDebug"></a> L'abilitazione di informazioni di debug avanzate  
 A causa delle interazioni talvolta complesse tra il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo (devenv.exe), il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo host (vssphost4.exe) SharePoint, SharePoint e il livello di WCF, la diagnosi di errori che si verificano durante la compilazione, distribuzione e così via può essere un richiesta di verifica. Per consentire di risolvere tali errori, è possibile abilitare le informazioni di debug avanzate. A tale scopo, passare alla chiave del Registro di sistema seguente del Registro di sistema:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 Se "EnableDiagnostics" **REG_DWORD** valore non esiste, crearla manualmente. Impostare il valore "EnableDiagnostics" su "1".  
  
 Impostazione del valore di chiave su stack cause 1 le informazioni di vengono visualizzati nella traccia di **Output** finestra ogni volta che si verificano errori di sistema di progetto quando si esegue [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per disabilitare le informazioni di debug avanzate, impostare EnableDiagnostics di nuovo su 0 oppure eliminare il valore.  
  
 Per ulteriori informazioni su altre chiavi del Registro di sistema di SharePoint, vedere [estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  