---
title: Quali sono le opzioni di pubblicazione più adatte? | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.reviewer: riande
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5927986b8c89a2e86fcecf874eae35ac016805f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# Quali sono le opzioni di pubblicazione più adatte?

Dall'interno di Visual Studio le applicazioni Web possono essere pubblicate direttamente nelle destinazioni seguenti:

- [Servizio app di Azure](#azure-app-service)
- [Macchine virtuali di Azure](#azure-virtual-machines)
- [File system](#file-system)
- [Destinazioni personalizzate (IIS, FTP e così via) ](#custom-targets), inclusi tutti i server Web arbitrari.

Nella scheda **Pubblica** è possibile selezionare un profilo di pubblicazione esistente, importare un profilo esistente o crearne uno nuovo usando le opzioni descritte di seguito. Per una panoramica delle opzioni di pubblicazione nell'IDE per diversi tipi di app, vedere [Presentazione della distribuzione](../../deployment/deploying-applications-services-and-components.md).

## App Web di Servizio app di Azure

Le [app Web di Servizio app di Azure](/azure/app-service/app-service-web-overview) (o semplicemente app Web) consentono agli sviluppatori di creare rapidamente un'ampia gamma di servizi e applicazioni Web scalabili senza gestire l'infrastruttura.

Per determinare la potenza di calcolo di un'app Web, scegliere un [piano tariffario](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) per il servizio app che la contiene. È possibile fare in modo che più app Web (e altri tipi di app) condividano lo stesso servizio app senza modificare il piano tariffario. Ad esempio, è possibile ospitare app Web di sviluppo, gestione temporanea e produzione insieme nello stesso servizio app.

Un servizio app viene eseguito nelle macchine virtuali ospitate nel cloud di Azure, ma tali macchine vengono gestite automaticamente. A ogni app Web di un servizio app verrà assegnato un URL \*.azurewebsites.net univoco. Tutti i piani tariffari diversi da quello gratuito consentono l'assegnazione di nomi di dominio personalizzati al sito.

### Quando scegliere le app Web di Servizio App di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet.
- Si vuole adeguare automaticamente l'applicazione Web in base alla richiesta senza doverla ridistribuire.
- Non si vuole gestire l'infrastruttura di server, inclusi gli aggiornamenti software.
- Non sono necessarie personalizzazioni a livello di computer sui server che ospitano l'applicazione Web.

> Per usare Servizio app di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Per altre informazioni sulla pubblicazione di app ASP.NET Core, vedere [Pubblicare un'app Web ASP.NET Core in Servizio app di Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## Macchine virtuali di Azure

Le [macchine virtuali (VM) di Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) consentono di creare e gestire qualsiasi numero di risorse di elaborazione nel cloud. Con l'assunzione della responsabilità per tutto il software e tutti gli aggiornamenti nelle macchine virtuali, è possibile personalizzare le macchine in base alle esigenze dell'applicazione Web. È possibile accedere alle macchine virtuali direttamente con Desktop remoto e ognuna di esse manterrà l'indirizzo IP assegnato finché lo si ritiene opportuno.

Il ridimensionamento di un'applicazione Web ospitata in macchine virtuali comporta l'attivazione di altre macchine virtuali in base alla richiesta e quindi la distribuzione del software necessario. Questo livello di controllo aggiuntivo consente di ridimensionare le macchine in modo diverso nelle diverse aree geografiche globali. Se ad esempio l'applicazione viene usata da dipendenti dislocati in varie sedi regionali, è possibile ridimensionare le macchine virtuali in base al numero di dipendenti di quelle sedi, potenzialmente riducendo i costi.

Per altre informazioni, vedere il [confronto dettagliato](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) tra Servizio app di Azure, Macchine virtuali di Azure e altri servizi di Azure che è possibile usare come destinazione della distribuzione usando l'opzione Personalizzata in Visual Studio.

### Quando scegliere Macchine virtuali di Azure

- Si vuole distribuire un'applicazione Web accessibile via Internet, con controllo completo della durata degli indirizzi IP assegnati.
- Sono necessarie personalizzazioni a livello di computer sui server, che includono software aggiuntivo come ad esempio un sistema di database specializzato, configurazioni di rete specifiche, partizioni del disco e così via.
- Si vuole garantire un elevato livello di controllo sul ridimensionamento dell'applicazione Web.
- È necessario l'accesso diretto ai server che ospitano l'applicazione per qualsiasi altro motivo.

> Per usare le macchine virtuali di Azure nel proprio centro dati o in altri computer locali, usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## File system

Effettuare la distribuzione nel file system significa semplicemente copiare i file dell'applicazione Web in una cartella specifica del proprio computer. Questo sistema viene spesso usato a scopo di test o per distribuire l'applicazione per l'uso destinato a un numero limitato di persone, se il computer esegue anche un server Web. Se la cartella di destinazione è condivisa in rete, la distribuzione nel file system può rendere disponibili i file dell'applicazione Web per altri utenti che possono distribuirli a loro volta a server specifici.

Qualsiasi computer locale che esegue un server Web è in grado di rendere l'applicazione disponibile su Internet o Intranet, in base al tipo di configurazione e alle reti a cui è connesso. Se si connette un computer direttamente a Internet, prestare particolare attenzione a proteggerlo dalle minacce esterne per la sicurezza. Poiché l'utente gestisce questi computer, ha il controllo completo delle configurazioni hardware e software.

Si noti che se per qualsiasi motivo (ad esempio, l'accesso al computer) non si è in grado di usare servizi cloud come Servizio app di Azure o Macchine virtuali di Azure, è possibile usare [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) nel proprio centro dati. Azure Stack consente di gestire e usare le risorse di elaborazione con Servizio app di Azure e Macchine virtuali di Azure, mantenendo tutti gli elementi in locale.

### Quando scegliere la distribuzione nel file system

- È necessario distribuire l'applicazione solo in una condivisione di file da cui altri utenti effettueranno a loro volta la distribuzione a server diversi.
- È necessaria solo una distribuzione locale dei test.
- Si vuole esaminare e potenzialmente modificare in modo indipendente i file dell'applicazione prima di inviarli a un'altra destinazione di distribuzione.

Per altre informazioni sulla distribuzione di app .NET Core, vedere [Distribuzione di app .NET Core con Visual Studio](/dotnet/core/deploying/deploy-with-vs).

## Destinazioni personalizzate

Una destinazione personalizzata consente di distribuire l'applicazione Web a una destinazione diversa da Servizio app di Azure, Macchine virtuali di Azure o il file system locale. È possibile distribuire l'applicazione a un file system o qualsiasi altro server (Internet o Intranet) a cui si ha accesso, inclusi quelli presenti in altri servizi cloud. È anche possibile usare una distribuzione Web (file o .ZIP) e FTP.

Quando si sceglie una destinazione personalizzata Visual Studio richiede un nome di profilo e quindi raccoglie ulteriori informazioni sulla **connessione** tra cui il server o il percorso di destinazione, un nome di sito e le credenziali. È possibile controllare i comportamenti seguenti nella scheda **Impostazioni**:

- La configurazione da distribuire.
- Se rimuovere i file esistenti dalla destinazione.
- Se precompilare durante la pubblicazione.
- Se escludere i file nella cartella App_Data dalla distribuzione.

Visual Studio consente di creare qualsiasi numero di profili di distribuzione personalizzata e di gestire i profili con impostazioni diverse.

### Quando scegliere una distribuzione personalizzata

- Se si usano servizi cloud di un provider diverso da Azure a cui è possibile accedere con URL.
- Si vuole eseguire la distribuzione usando credenziali diverse da quelle usate in Visual Studio o quelle associate direttamente all'account Azure.
- Si vuole eliminare i file dalla destinazione ogni volta che si esegue la distribuzione.

Per altre informazioni sulla pubblicazione in IIS, vedere [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (Uso di ASP.NET 3.5 e ASP.NET 4.5 in IIS 8.0) e [Remote Debug ASP.NET on a Remote IIS Computer](../../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) (Debug remoto di ASP.NET in un computer IIS remoto).