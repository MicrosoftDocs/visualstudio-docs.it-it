---
title: Usare un ambiente lab per DevOps | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: lab environment, test lab
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 227068197de1d953ae6f3729888a1b6d2dfc164c
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="use-a-lab-environment-for-your-devops"></a>Usare un ambiente lab per DevOps

Un ambiente lab è una raccolta di computer virtuali e fisici che è possibile usare per sviluppare e testare le applicazioni. Un ambiente lab può contenere più ruoli necessari per testare le applicazioni a più livelli, come le workstation, i server Web e i server database. Inoltre, è possibile usare un flusso di lavoro compilazione, distribuzione e test con l'ambiente lab per automatizzare il processo di compilazione, distribuzione ed esecuzione di test automatizzati sull'applicazione.

* **Usare un piano di test per eseguire test automatizzati**: è possibile eseguire una raccolta di test automatizzati, denominata *piano di test*, e visualizzarne lo stato.  
  
* **Usare un flusso di lavoro di compilazione/distribuzione/test**: è possibile usare un flusso di lavoro di compilazione/distribuzione/test per testare automaticamente le applicazioni multilivello. Un esempio tipico è un flusso di lavoro che avvia una compilazione, distribuire i file di compilazione sui computer appropriati in un ambiente lab e quindi esegue test automatizzati. È anche possibile pianificare l’esecuzione del flusso di lavoro a intervalli specifici.  
  
* **Raccogliere dati diagnostici da tutti i computer anche durante i test manuali**: è possibile raccogliere simultaneamente test diagnostici da più computer. Ad esempio, durante una singola esecuzione dei test è possibile raccogliere dati IntelliTrace, impatto test e altre forme di dati da un server Web, un server di database e un client.  
  
Ecco alcuni esempi di tipi comuni di ambienti lab:  
  
| Topologia | Descrizione |  
|---|---|  
|![Topologia solo server](../media/topology_backend.png)| Questo ambiente lab ha una *topologia server*, che è spesso usata per eseguire test manuali su applicazioni server e che consente ai tester di usare i propri computer client per verificare i bug nell'ambiente. In una topologia di back-end, l'ambiente lab contiene solo i server. Quando si usa questo tipo di topologia in genere si esegue la connessione ai server nell’ambiente lab usando un computer client che non fa parte dell’ambiente.|  
|![Ambiente lab nel cloud](../media/topology_cloud.png)| Questo ambiente lab presenta caratteristiche e funzionalità simili alla _topologia server_ senza il requisito della presenza di macchine virtuali o computer fisici in un ambiente locale. Ciò può ridurre la durata della configurazione, semplificare la manutenzione e abbassare i costi. La configurazione di più siti Web e più macchine virtuali e la personalizzazione della rete sono semplici e rapide in un ambiente cloud come Microsoft Azure. [Altri dettagli](#usebandrm).|  
|![Ambiente lab client-server](../media/topology_clientserver.png)| Questo ambiente lab ha una *topologia client/server*, spesso usata per testare un'applicazione dotata di componenti server e client. In una topologia client/server tutti i computer client e server usati per testare l’applicazione si trovano nell’ambiente lab. Quando si usa questa topologia, è possibile raccogliere dati di test da ogni computer che incide sui test.|  
  
Vedere [Video: Managing lab environments for testing](http://go.microsoft.com/fwlink/?LinkID=252614) (Gestione degli ambienti lab per l'esecuzione di test).  
  
Ecco le tecniche più comuni per la configurazione di un ambiente lab: 
  
* **[Uso del cloud con Team Services o Team Foundation Server Build &amp; Release](#usebandrm)**

* **[Uso delle funzionalità di Visual Studio Lab Management di Microsoft Test Manager](#usemtmlm)**

<a name="usebandrm"></a>
## <a name="use-the-cloud-with-team-services-or-team-foundation-server-build-amp-release"></a>Usare il cloud con Team Services o Team Foundation Server Build &amp; Release

È possibile eseguire test automatizzati e automatizzare le operazioni di compilazione/distribuzione/test tramite la funzionalità [Build &amp; Release](https://www.visualstudio.com/team-services/continuous-integration/) presente in Team Foundation Server (TFS) e Visual Studio Team Services. Ecco alcuni dei vantaggi che offre:

* Non è necessario alcun controller di compilazione o di test.
* L'agente di test viene installato tramite un'attività compresa nella compilazione o nella versione.
* È facile personalizzare i passaggi di distribuzione. È ora possibile usare più di uno script. È anche possibile usufruire delle numerose attività disponibili nel prodotto e in Visual Studio Marketplace.
* Non è necessario gestire gruppi di test. È possibile eseguire i test direttamente dai file binari.
* Per i test eseguiti all'interno di ogni compilazione o di ogni versione è possibile ottenere un'esperienza di report inline più esaustiva.
* È possibile tenere traccia delle risorse (versione, compilazione, elementi di lavoro, commit) distribuite e sottoposte a test in ogni ambiente.
* È possibile personalizzare ed estendere l'automazione per distribuire con facilità più ambienti di test e persino l'ambiente di produzione.
* È possibile pianificare l'automazione in modo che venga eseguita ogni volta che viene effettuata un'archiviazione o un commit oppure ogni giorno a un'ora specifica.

[Altre informazioni](use-build-or-rm-instead-of-lab-management.md).

<a name="usemtmlm"></a>
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Usare le funzionalità di Visual Studio Lab Management di Microsoft Test Manager

È possibile creare e gestire ambienti lab con le funzionalità di Visual Studio Lab Management di Microsoft Test Manager quando si usa Visual Studio Enterprise o Visual Studio Test Professional.

Lab Management installa automaticamente agenti di test in ogni computer dell'ambiente.  
  
Se si usa il servizio Lab Management in concomitanza con System Center Virtual Machine Manager (SCVMM), è possibile ottenere questi vantaggi anche quando si usano gli ambienti lab:  
  
* **Riprodurre rapidamente le configurazioni dei computer**: è possibile archiviare raccolte di macchine virtuali configurate in modo da ricreare tipici ambienti di produzione. Sarà quindi possibile procedere a ciascuna esecuzione dei test in una nuova copia di un ambiente archiviato.  
  
* **Riprodurre esattamente le condizioni di un bug**: quando l'esecuzione dei test ha esito negativo, è possibile archiviare una copia dello stato dell'ambiente lab e accedervi dai risultati di compilazione o da un elemento di lavoro.  
  
* **Eseguire più copie di un ambiente lab allo stesso tempo**: è possibile eseguire più copie dell'ambiente lab contemporaneamente senza conflitti di denominazione.  
  
### <a name="standard-environments-and-scvmm-environments"></a>Ambienti standard e ambienti SCVMM

Con Visual Studio Lab Management è possibile creare due tipi di ambiente lab: **ambienti standard** e **ambienti SCVMM**.
Tuttavia, le funzionalità di ogni tipo di ambiente sono diverse.  
  
> **NOTA**: Lab Management **non** supporta SCVMM 2016. Per informazioni su SCVMM, vedere [Virtual Machine Manager](http://go.microsoft.com/fwlink/?LinkId=226332). 
  
**Ambienti standard:** possono contenere una combinazione di computer fisici e macchine virtuali. È anche possibile aggiungere macchine virtuali a un ambiente standard, gestite da framework di virtualizzazione di terze parti. Inoltre, gli ambienti standard non richiedono risorse server aggiuntive, come un server SCVMM.  
  
**Ambienti SCVMM:** possono contenere solo macchine virtuali gestite da SCVMM (System Center Virtual Machine Manager), quindi le macchine virtuali in ambienti SCVMM possono essere eseguite solo su framework di virtualizzazione Hyper-V. Tuttavia, gli ambienti SCVMM forniscono le seguenti funzionalità di gestione e di automazione non disponibili in ambienti standard:  
  
- **Snapshot dell'ambiente:** gli snapshot dell'ambiente contengono lo stato di un ambiente lab. È quindi possibile ripristinare rapidamente un ambiente pulito o salvare lo stato di un ambiente modificato. È anche possibile usare un flusso di lavoro di compilazione-distribuzione-test per automatizzare il processo di salvataggio e ripristino degli snapshot dell'ambiente.  
  
- **Ambienti archiviati:** è possibile archiviare una copia di un ambiente SCVMM e quindi distribuirne più copie.  
  
- **Isolamento rete:** l'isolamento rete consente di eseguire contemporaneamente più copie identiche di un ambiente SCVMM senza conflitti di nomi computer.  
  
- **Modelli di macchina virtuale:** un modello di macchina virtuale è una macchina virtuale il cui nome e altri identificatori sono stati rimossi. Quando un modello di macchina virtuale viene distribuito in un ambiente SCVMM, Microsoft Test Manager genera nuovi identificatori. Ciò consente di distribuire più copie di una macchina virtuale nello stesso ambiente o in più ambienti e quindi eseguire le macchine virtuali contemporaneamente.  
  
- **Macchine virtuali archiviate:** una macchina virtuale archiviata nella libreria del progetto team e che include identificatori univoci.  
  
Per informazioni su queste funzionalità, vedere [Linee guida per la creazione e la gestione di ambienti SCVMM](https://msdn.microsoft.com/en-gb/library/ee830480.aspx).  
  
Gli ambienti standard e gli ambienti SCVMM supportano molte delle stesse funzionalità. Esistono tuttavia alcune importanti differenze da considerare. Nella tabella seguente vengono confrontate le funzionalità disponibili per gli ambienti standard e gli ambienti SCVMM.  
  
|Funzionalità|Ambienti SCVMM|Ambienti standard|  
|----------------|------------------------|---------------------------|  
|**Test**|||  
|Eseguire test manuali|Supportato|Supportato|  
|Eseguire il test codificato dell'interfaccia utente e altri test automatizzati|Supportato|Supportato|  
|Archiviare bug dettagliati usando gli adattatori diagnostici|Supportato|Supportato|  
|**Distribuzione della compilazione**|||  
|Flussi di lavoro compilazione, distribuzione e test automatici|Supportato|Supportato|  
|**Creazione e gestione dell'ambiente**|||  
|Usare computer fisici oltre alle macchine virtuali|Non supportato|Supportato|  
|Usare macchine virtuali di terze parti|Non supportato|Supportato|  
|Installazione automatica degli agenti di test nei computer nell'ambiente lab|Supportato|Supportato|  
|Salvare e distribuire lo stato di un ambiente lab tramite snapshot dell'ambiente|Supportato|Non supportato|  
|Creare ambienti lab dai modelli di macchina virtuale|Supportato|Non supportato|  
|Avviare, arrestare e creare lo snapshot dell'ambiente|Supportato|Non supportato|  
|Connettersi all'ambiente usando Visualizzatore ambiente|Supportato|Supportato|  
|Eseguire più copie di un ambiente nello stesso momento usando l'isolamento della rete|Supportato|Non supportato|  
  
### <a name="lab-management-concepts"></a>Concetti di Lab Management

Di seguito sono riportati alcuni concetti aggiuntivi che è necessario conoscere prima di continuare:  
  
|Termine|Descrizione|  
|----------|-----------------|  
|Centro Lab|L'area di Microsoft Test Manager in cui creare e gestire ambienti lab.|  
|Lab del progetto team|La raccolta di ambienti lab che sono stati configurati in modo da connettersi a essi ed eseguire le macchine virtuali.|  
|Libreria del progetto team|Un archivio delle macchine virtuali archiviate, modelli e ambienti lab archiviati che sono stati importati nel gruppo host del progetto team. È possibile usare gli elementi della raccolta con ambienti SCVMM, tuttavia non è possibile aggiungerli direttamente in un ambiente standard. Non è possibile eseguire gli elementi della raccolta, ma è possibile usarli per implementare un nuovo ambiente.|  
|Ambiente distribuito|Un ambiente che è stato distribuito nel lab del progetto team per connettersi ed eseguire i relativi computer.|  

#### <a name="related-topics"></a>Argomenti correlati

* [Pianificare il lab](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx) 
* [Configurazione e amministrazione di Lab Management](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx) 
* [Configurazione di Lab Management per ambienti SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx) 
* [Aggiornamento di SCVMM 2008 R2 a SCVMM 2012](upgrade-scvmm-2008-r2-scvmm-2012.md) 
* [Gestire autorizzazioni](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx) 
* [Modifica della configurazione](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx) 
* [Risoluzione dei problemi](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)
  
### <a name="set-up-environments"></a>Impostare gli ambienti

* [Ambienti cloud Build &amp; Release](use-build-or-rm-instead-of-lab-management.md)
* [Ambienti lab standard](https://msdn.microsoft.com/en-gb/library/ee390842.aspx)
* [Ambienti SCVMM (virtuali)](https://msdn.microsoft.com/en-gb/library/ee943322.aspx)
* [Creazione e uso di un ambiente di isolamento rete](https://msdn.microsoft.com/en-gb/library/ee518924.aspx)
  
## <a name="see-also"></a>Vedere anche
  
* [Installare e configurare agenti di test](install-configure-test-agents.md)
* [Visual Studio Lab Management Guide](http://go.microsoft.com/fwlink/?LinkID=230951) (Guida di Visual Studio Lab Management)  
* [Managing lab environments for testing](http://go.microsoft.com/fwlink/?LinkID=252614) (Gestione degli ambienti lab per l'esecuzione di test)  
* [Blog di Visual Studio DevOps e Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
