---
title: Profilatura delle prestazioni delle applicazioni di SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 44c2566a722794fea176100db144f09c6c010f6e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>Profilatura delle prestazioni di applicazioni di SharePoint
 
Se si eseguono le applicazioni di SharePoint in modo non efficiente o lentamente, è possibile utilizzare la funzionalità di profilatura in Visual Studio per identificare i problemi con il codice e altri elementi. Tramite il funzionalità di test di carico, è possibile determinare le prestazioni di un'applicazione di SharePoint in condizioni di carico, ad esempio quando molti utenti accedono all'applicazione contemporaneamente. Eseguendo i test delle prestazioni web, è possibile misurare la modalità con cui l'applicazione esegue sul web. Tramite i test codificati dell'interfaccia utente, è possibile verificare se l'intera applicazione di SharePoint, compresa l'interfaccia utente, funzioni correttamente. Quando si utilizzano insieme questi test, si consente di identificare i problemi di prestazioni prima di distribuire l'applicazione.

## <a name="profiling-tools-overview"></a>Panoramica degli strumenti di profilatura

Profilatura si intende il processo di analisi e registrare il comportamento delle prestazioni dell'applicazione mentre è in esecuzione. Per la profilatura dell'applicazione, si possono rivelare problemi come i colli di bottiglia, codice inefficiente e problemi di allocazione di memoria, che causano rallentamenti o usano troppa memoria. Ad esempio, è possibile utilizzare profilatura per identificare le aree sensibili nel codice, ovvero i segmenti di codice che vengono chiamati frequentemente e possono rallentare le prestazioni complessive dell'applicazione. Dopo aver identificato le aree sensibili, è spesso possibile ottimizzare o eliminarli.

È possibile utilizzare diversi strumenti di profilatura nell'ambiente di sviluppo integrato (IDE) per identificare e individuare questi tipi di problemi di prestazioni. Questi strumenti funzionano allo stesso modo per progetti SharePoint, come avviene per altri tipi di progetti di Visual Studio. Guidata prestazioni degli strumenti di profilatura guidano la creazione di una sessione di prestazioni che utilizza i test desiderati. Una sessione di prestazioni è un set di dati di configurazione che viene utilizzati per raccogliere informazioni sulle prestazioni da un'applicazione, insieme ai risultati di uno o più esecuzioni della profilatura. Sessioni di prestazioni vengono archiviate nella cartella del progetto e, è possibile visualizzarli in **Esplora prestazioni**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](/visualstudio/profiling/understanding-performance-collection-methods).

Dopo aver creato e si esegue un'analisi di profilo sull'applicazione, un report include informazioni dettagliate sulle prestazioni. Questo report può includere elementi, ad esempio un grafico di utilizzo della CPU nel tempo, uno stack di chiamate di funzione gerarchici o in un albero delle chiamate. Il contenuto esatto del report può variare a seconda del tipo di test che si esegue, ad esempio campionamento o strumentazione. Per ulteriori informazioni, vedere [Report panoramica degli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Processo della sessione di prestazioni

Per profilare un'applicazione, è necessario innanzitutto utilizzando la procedura guidata di profilatura delle prestazioni strumenti per creare una sessione di prestazioni. Nella barra dei menu, scegliere **Analizza**, **Avvia Creazione guidata sessione di prestazioni**. Dopo avere completato la procedura guidata, immettere le informazioni necessarie per la sessione di prestazioni, ad esempio il metodo di profilo che si desidera e l'applicazione che si desidera profilare. Per ulteriori informazioni, vedere [procedura: profilare un sito Web o applicazione Web mediante la creazione guidata prestazioni](http://go.microsoft.com/fwlink/?LinkId=224692). In alternativa, è possibile utilizzare le opzioni della riga di comando per configurare ed eseguire una sessione di prestazioni. Per ulteriori informazioni, vedere [utilizzando la profilatura strumenti dal della riga di comando](http://go.microsoft.com/fwlink/?LinkId=224703). Se si desidera configurare manualmente ogni aspetto di una sessione di prestazioni, vedere [procedura: creare manualmente di sessioni di prestazioni con gli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224691). È inoltre possibile creare in una sessione di prestazioni da uno unit test, il **risultati Test** finestra, aprire il menu di scelta rapida per lo unit test e quindi scegliendo **Crea sessione prestazioni**.


Dopo aver impostato una sessione di prestazioni, la configurazione di sessione viene salvata, il server è configurato per fornire dati di profilatura e viene eseguita l'applicazione. Quando si utilizza l'applicazione, i dati sulle prestazioni sono scritto in un file di log. Sessioni di prestazioni sono elencate **Esplora prestazioni** sotto il **destinazioni** cartella. Al termine di una sessione di prestazioni, il report viene visualizzato nel **report** cartella **Esplora prestazioni**. Per visualizzare il report, aprire il file in **Esplora prestazioni**. Per visualizzare o configurare le proprietà di una sessione di prestazioni, aprire il menu di scelta rapida in **Esplora prestazioni**, quindi scegliere **proprietà**. Per ulteriori informazioni su proprietà specifiche di una sessione di prestazioni, vedere [la configurazione di sessioni di prestazioni per gli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224694). Per informazioni su come interpretare i risultati di una sessione di prestazioni, vedere [analisi dei dati degli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-testing"></a>Test di stress

È possibile analizzare le prestazioni di stress delle applicazioni mediante la creazione di test di carico e test delle prestazioni web in Visual Studio. Quando si crea un test di carico in Visual Studio, specificare una combinazione di fattori, chiamato per testare l'applicazione rispetto a uno scenario. Che includono il modello di carico, modello di combinazione di test, combinazione di test, la combinazione di reti e combinazione di web browser. Scenari di test di carico possono includere sia unit test e test delle prestazioni web.

Nella figura 1: Esempio di risultati dei test di carico

![Visualizzazione di grafici di esecuzione test di carico](../sharepoint/media/load-webgraphs.png "visualizzazione grafici di esecuzione test di carico")

Test delle prestazioni Web per simulare come un utente finale può interagire con un'applicazione di SharePoint. È possibile creare test delle prestazioni web registrando le richieste HTTP in una sessione del browser o tramite il **registrazione Test prestazioni Web**. Le richieste web vengono visualizzati di **Editor Test prestazioni Web** al termine della sessione del browser. È quindi possibile eseguire il debug i risultati di **Visualizzatore risultati Test di prestazioni Web**. È possibile creare anche manualmente i test delle prestazioni web utilizzando il **Editor Test prestazioni Web**.

## <a name="testing-user-interfaces"></a>Test delle interfacce utente

I test codificati dell'interfaccia utente unità automaticamente l'applicazione di SharePoint tramite l'interfaccia utente (UI). Questi test riguardano i controlli dell'interfaccia utente, ad esempio i pulsanti e menu, verificare che funzionino correttamente. Questo tipo di test è particolarmente utile se la convalida o logica di altro viene eseguita nell'interfaccia utente, ad esempio in una pagina web. È anche possibile utilizzare i test codificati dell'interfaccia utente per automatizzare i test manuali. Creazione di test codificati dell'interfaccia utente per le applicazioni di SharePoint nello stesso modo durante la creazione di test per altri tipi di applicazioni. Per ulteriori informazioni, vedere [test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: profilatura di un'applicazione di SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Viene illustrato come eseguire un'analisi di profilo di campionamento in un'applicazione di SharePoint.|
|[Eseguire il test delle prestazioni dell'applicazione prima del rilascio](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|Viene descritto come creare un test di carico, che consentono di applicazioni di SharePoint del test di stress.|
|[Eseguire unit test del codice](/visualstudio/test/unit-test-your-code)|Viene descritto come individuare gli errori di logica nel codice tramite unit test.|
|[Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|Descrive come testare l'interfaccia utente delle applicazioni SharePoint.|

## <a name="see-also"></a>Vedere anche

[Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)