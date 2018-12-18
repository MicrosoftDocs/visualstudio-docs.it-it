---
title: IntelliTrace | Documenti Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 07afad8b464e266477c4edbb97ffc3eb3d8436e4
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="intellitrace"></a>IntelliTrace

È possibile ridurre il tempo richiesto per eseguire il debug dell'applicazione quando si usa IntelliTrace per registrare e tenere traccia della cronologia di esecuzione del codice. È possibile trovare facilmente i bug perché IntelliTrace consente di:

- Registrare eventi specifici

     Esaminare il codice correlato, i dati visualizzati nel **variabili locali** finestra durante gli eventi del debugger e le informazioni di chiamata di funzione

- Eseguire il debug di errori difficili da riprodurre o verificatisi in fase di distribuzione

È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="what-do-you-want-to-do"></a>Selezionare l'operazione da eseguire.

|||
|-|-|
|**Eseguire il debug dell'applicazione con IntelliTrace:**<br /><br /> -Mostra gli eventi passati.<br />-Mostra me chiamare informazioni con gli eventi passati.<br />-Salva la sessione di IntelliTrace.<br />-Controllare i dati raccolti da IntelliTrace.|- [Procedura dettagliata: Utilizzo di IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)<br />- [Il debug cronologico](../debugger/historical-debugging.md)<br />- [Visualizzare gli snapshot utilizzando IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md)|
|**Raccogliere dati IntelliTrace durante una sessione di test in Test Manager**|- [Raccogliere più dati di diagnostica durante i test manuali](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Raccogliere dati IntelliTrace dalle applicazioni distribuite**|- [Tramite l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Avviare il debug da un file di log IntelliTrace (file con estensione iTrace).**|- [Utilizzando i dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> Quali App è possibile eseguire il debug con IntelliTrace?

|||
|-|-|
|**Supportato**|-Visual Basic e Visual c# applicazioni che utilizzano .NET Framework 2.0 o versioni successive.<br/>È possibile eseguire il debug della maggior parte delle applicazioni, comprese le app ASP.NET, Microsoft Azure, Windows Form, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 e a 64 bit.<br/>Per eseguire il debug di applicazioni di SharePoint con IntelliTrace, vedere [procedura dettagliata: debug di un'applicazione SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Per eseguire il debug di applicazioni di Microsoft Azure con IntelliTrace, vedere [debug di un servizio Cloud pubblicato con IntelliTrace e Visual Studio](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services).|
|**Supporto limitato**|-.NET core e le applicazioni ASP.NET Core è supportate solo per gli eventi<br />-App F # su base sperimentale<br />-Le app UWP supportate solo per gli eventi|
|Non è supportato|-C++, altri linguaggi e script<br />-Servizi, Silverlight, Xbox o [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] App|

> [!NOTE]
> Se si desidera eseguire il debug di un processo già in esecuzione, è possibile raccogliere solo gli eventi IntelliTrace (nessuna informazione di chiamata). È possibile collegare a un processo a 32 o 64 bit del computer locale. Non vengono raccolti gli eventi che si verificano prima connettersi al processo.

##  <a name="IntelliTraceVSTraditional"></a> Perché eseguire il debug con IntelliTrace?

Tradizionali o *live* debug Mostra solo stato dell'applicazione corrente, con dati limitati sugli eventi passati. È necessario dedurre tali eventi dallo stato corrente dell'applicazione oppure ricrearli rieseguendo l'applicazione.

IntelliTrace consente di espandere questa esperienza di debug tradizionale registrando dati ed eventi specifici in un preciso momento. Ciò consente di verificare cosa sia accaduto nell'applicazione senza riavviarla, specialmente se si supera il punto in cui si è verificato il bug. IntelliTrace è attivato per impostazione predefinita durante il debug tradizionale e raccoglie i dati in modo automatico e invisibile. Ciò consente di passare facilmente dal debug tradizionale al debug IntelliTrace e viceversa per visualizzare le informazioni registrate. Vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md) e [quali dati raccoglie IntelliTrace?](#WhatData)

IntelliTrace consente anche di eseguire il debug di errori difficili da riprodurre o che si verificano in fase di distribuzione. È possibile raccogliere dati IntelliTrace e salvarli in un file di log IntelliTrace (file .iTrace), contenente dettagli su eccezioni, eventi di prestazioni, richieste Web, dati di test, thread, moduli e altre informazioni di sistema. È possibile aprire questo file in Visual Studio Enterprise, selezionare un elemento e avviare il debug con IntelliTrace. Ciò consente di passare a qualsiasi evento nel file e visualizzare dettagli specifici sull'applicazione in un dato momento.

È possibile salvare i dati IntelliTrace dalle seguenti origini:

- Una sessione di IntelliTrace in Visual Studio 2017 Enterprise, Visual Studio 2015 Enterprise o versioni precedenti di Visual Studio Ultimate.

- Una sessione di test in Microsoft Test Manager

- App Web ASP.NET ospitate in IIS o applicazioni SharePoint 2010 e SharePoint 2013 in esecuzione nella distribuzione quando si usa Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012. Vedere [utilizzare l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) e [monitoraggio con Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

 Di seguito sono riportati alcuni esempi sul modo in cui IntelliTrace semplifica le operazioni di debug:

- L'applicazione ha danneggiato un file di dati, ma non si sa dove si è verificato l'evento.

     Senza IntelliTrace, sarebbe necessario esaminare il codice per trovare tutti gli accessi possibili al file, inserire punti di interruzione in corrispondenza di tali accessi e quindi rieseguire l'applicazione per individuare dove si è verificato il problema. Con IntelliTrace è possibile vedere tutti gli eventi di accesso ai file raccolti e dettagli specifici sull'applicazione nel momento in cui si è verificato ciascun evento.

- Si verifica un'eccezione.

     Senza IntelliTrace, viene visualizzato un messaggio su un'eccezione, ma non si dispone di una quantità di informazioni sugli eventi che ha causato l'eccezione. È possibile esaminare lo stack di chiamate per individuare la catena di chiamate che ha causato l'eccezione, ma non è possibile visualizzare la sequenza di eventi che si sono verificati durante tali chiamate. Con IntelliTrace è possibile esaminare gli eventi che si sono verificati prima dell'eccezione.

- L'applicazione si arresta in modo anomalo in un computer utilizzato per i test, ma viene eseguita correttamente in un computer di sviluppo.

     È possibile raccogliere dati IntelliTrace da Microsoft Test Manager, salvare i dati in un file .iTrace e allegarlo a un elemento di lavoro Team Foundation Server per analizzarlo in un secondo momento. Vedere [raccogliere più dati di diagnostica durante i test manuali](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests) e [utilizzare dati di IntelliTrace salvato](../debugger/using-saved-intellitrace-data.md).

- Un bug o un arresto anomalo si verifica in un'applicazione distribuita.

     Per le app basate su Microsoft Azure, è possibile configurare la raccolta di dati IntelliTrace prima di pubblicare l'applicazione. Mentre l'applicazione è in esecuzione, IntelliTrace salva i dati in un file .iTrace. Vedere [eseguire il Debug di un servizio Cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).

     Per le app Web ASP.NET ospitate in IIS 7.0, 7.5 e 8.0 o le applicazioni SharePoint 2010 o SharePoint 2013, utilizzare Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012, per salvare i dati IntelliTrace in un file .iTrace.

     Si tratta di un'opzione utile per diagnosticare problemi con le app in fase di distribuzione. Vedere [utilizzare l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> Quali dati raccoglie IntelliTrace?

**Raccogliere informazioni sugli eventi**

Per impostazione predefinita, IntelliTrace registra solo gli eventi di IntelliTrace: eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema utili per il debug. È possibile scegliere i tipi di eventi IntelliTrace che si desidera raccogliere, tranne gli eventi del debugger e le eccezioni, che vengono sempre raccolti. Vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md).

- **Eventi del debugger**

     IntelliTrace registra sempre gli eventi che si verificano nel debugger di Visual Studio. Ad esempio, l'avvio dell'applicazione è un evento del debugger. Altri eventi del debugger sono eventi di arresto, ossia quelli che interrompono l'esecuzione dell'applicazione, Ad esempio, il programma raggiunge un punto di interruzione, raggiunge un punto di analisi o viene eseguito un **passaggio** comando.

     Per impostazione predefinita, per migliorare le prestazioni, IntelliTrace non registra ogni possibile valore per un evento del debugger. Vengono invece registrati questi valori:

    - I valori di **variabili locali** finestra. Mantenere il **variabili locali** finestra aperta per visualizzare questi valori.

    - I valori di **Auto** solo se finestra il **Auto** finestra è aperta

    - Valori nei suggerimenti dati mostrati quando si sposta il puntatore del mouse su una variabile nella finestra di origine per visualizzarne il valore. Tramite IntelliTrace non vengono raccolti i valori nei suggerimenti dati bloccati.

    Quando è abilitata la modalità di eventi IntelliTrace e snapshot, IntelliTrace verrà creare uno snapshot del processo dell'applicazione in ogni debugger **punto di interruzione** e **passaggio** evento. Questo registrerà i valori di **variabili locali**, **Auto**, e **espressioni di controllo** windows, indipendentemente dal fatto di windows siano aperte. Verranno raccolti anche i valori in tutti i suggerimenti dati bloccati.

- **Eccezioni**

     Tramite IntelliTrace vengono registrati il tipo di eccezione e il messaggio per questi tipi di eccezione:

    - Eccezioni gestite in cui l'eccezione viene generata e rilevata

    - Eccezioni non gestite

- **Eventi di .NET framework**

     Per impostazione predefinita, tramite IntelliTrace vengono registrati gli eventi .NET Framework più comuni. Ad esempio:

    - Per un evento di verifica della casella di controllo, raccoglie lo stato e il testo della casella di controllo.

- **Eventi dell'applicazione SharePoint 2010 e SharePoint 2013**

     È possibile registrare eventi di profili utente e un subset di eventi del sistema di registrazione unificato per le applicazioni SharePoint 2010 e 2013 in esecuzione all'esterno di Visual Studio. È possibile salvare questi eventi in un file .iTrace. Richiede Visual Studio Enterprise 2017, Visual Studio Enterprise 2015, una versione precedente di Visual Studio Ultimate o [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) in esecuzione in **traccia** modalità.

     Quando si apre il file .iTrace, immettere un ID di correlazione SharePoint per trovare la richiesta Web corrispondente, visualizzare gli eventi registrati e avviare il debug da un evento specifico. Se il file contiene eccezioni non gestite, è possibile scegliere un ID di correlazione per avviare il debug di un'eccezione.

     Vedere:

    - [Usare l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Usare i dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)

    - [Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Acquisire snapshot**

È possibile configurare IntelliTrace per acquisire snapshot a ogni punto di interruzione e l'evento di passaggio del debugger. IntelliTrace registra lo stato dell'applicazione completo in ogni snapshot, che consente di visualizzare le variabili complesse e per valutare le espressioni.

Vedere [visualizzare snapshot tramite IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md).

**Raccogliere informazioni sulla chiamata di funzione**

È possibile configurare IntelliTrace per la raccolta delle informazioni sulle chiamate per le funzioni. Tali informazioni consentono di visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice. Per ogni chiamata di funzione, IntelliTrace registra i seguenti dati:

- Nome della funzione
- Valori dei tipi di dati primitivi passati come parametri nei punti di ingresso di una funzione e restituiti nei punti di uscita
- Valori delle proprietà automatiche quando vengono letti o modificati
- Puntatori agli oggetti figlio di primo livello, ma non ai relativi valori, se non quelli che indicano se lo stato è null oppure no

> [!NOTE]
> IntelliTrace raccoglie solo i primi 256 oggetti in matrici e i primi 256 caratteri per le stringhe.

Vedere [controllare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md).

**Raccogliere informazioni sul modulo**

Per controllare la quantità di informazioni sulle chiamate raccolte da IntelliTrace, specificare solo i moduli di interesse. In questo modo è possibile migliorare le prestazioni dell'applicazione durante la raccolta. Vedere la sezione [controllare la quantità di informazioni raccolte da IntelliTrace](../debugger/intellitrace-features.md#ControlCallData) nelle funzionalità di IntelliTrace.

## <a name="AffectPerformance"></a> IntelliTrace rallenterà l'applicazione?

Per impostazione predefinita, vengono raccolti dati solo per eventi di IntelliTrace selezionati. Ciò può rallentare o meno l'applicazione, a seconda della struttura e dell'organizzazione del codice. Ad esempio, se IntelliTrace registra spesso un evento, questo potrebbe rallentare l'applicazione. Potrebbe essere opportuno anche considerare il refactoring dell'applicazione.

La raccolta di informazioni sulle chiamate potrebbe rallentare significativamente l'applicazione. Potrebbero inoltre aumentare le dimensioni di ogni file di log IntelliTrace (file con estensione iTrace) salvato nel disco. Per ridurre al minimo questi effetti, raccogliere le informazioni sulle chiamate solo per i moduli desiderati.  Per modificare le dimensioni massime del file. iTrace, passare a **strumenti**, **opzioni**, **IntelliTrace**, **avanzate**. 

## <a name="in-this-section"></a>Contenuto della sezione

[Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)
[diagnosticare i problemi dopo la distribuzione](../debugger/diagnose-problems-after-deployment.md)
[utilizzare dati di IntelliTrace salvato](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Blog

[Visual Studio ALM e Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)

### <a name="forums"></a>Forum

[Diagnostica di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)