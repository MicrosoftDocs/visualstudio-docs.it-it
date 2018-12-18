---
title: Requisiti del test controller e dell'agente di test per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 1c6ae9d8200d6e8f32b7f8a96b222b4bfb4c75d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Requisiti del controller di test e dell'agente di test per il test di carico

In Visual Studio sono integrati diversi tipi di test, tra cui unit test, test prestazioni Web, test di carico e test manuali. Visual Studio consente agli utenti di Visual Studio Application Lifecycle Management di eseguire test sui computer remoti usando un test controller e uno o più agenti. Vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

## <a name="hardware-and-software-requirements"></a>Requisiti hardware e software

I computer del controller di test e dell'agente di test presentano requisiti hardware e software specifici. Se si desidera inoltre distribuire i computer del controller e dell'agente di test in più lingue, è necessario pianificare il supporto di tali lingue.

### <a name="hardware-requirements"></a>Requisiti hardware

Nella tabella seguente sono riportati i requisiti hardware consigliati per la distribuzione di un controller di test e di agenti di test.

|**Configurazione**|**Componente**|**CPU**|**Disco rigido**|**Memoria**|
|-----------------------|-------------------|-------------|------------|----------------|
|< 500 utenti virtuali|Agente di test|2,6 GHz|10 GB|2 GB|
|< 1000 utenti virtuali|Agente di test|Processore doppio, 2,6 GHz|10 GB|2 GB|
|N x 1000 utenti virtuali|Agente di test|Scalabilità orizzontale fino a N agenti, ognuno con processore doppio a 2,6 Ghz|10GB|2GB|
|\< 30 computer nell'ambiente di test. Include agenti e server sottoposti a test.|Test Controller|2,6 GHz|||
|N x 30 computer nell'ambiente di test. Include agenti e server sottoposti a test.|Test Controller|N processori a 2,6 GHz|||

> [!NOTE]
> Il numero di utenti virtuali varia notevolmente da test a test. Una delle cause principali di questa varianza è attribuibile ai *tempi interazione utente* o ritardi utente. Per altre informazioni, vedere [Modifica dei tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md). In un test di carico i test Web sono generalmente più efficienti e generano un carico maggiore rispetto agli unit test. I numeri nella tabella precedente sono validi per l'esecuzione di test Web con tempi interazione utente di 3-5 secondi in una tipica applicazione Web.

Le linee guida riportate qui vengono fornite a titolo generale per la pianificazione hardware. Le prestazioni del test variano notevolmente a seconda della quantità di dati di test e del numero di agenti di test. Per gli agenti di test la velocità della CPU e la memoria disponibile limitano il carico di test. I controller di test necessitano di risorse maggiori a seconda del numero di agenti di test e della quantità di dati coinvolti nei test.

Il server nel quale è in esecuzione Visual Studio deve avere una connessione di rete affidabile con una larghezza di banda minima di 1 Mbps e una latenza massima di 350 ms. Tra gli agenti di test e il controller di test non devono essere presenti firewall. Se le prestazioni del test non soddisfano le aspettative, si consiglia di aggiornare la configurazione hardware.

### <a name="additional-hardware-considerations"></a>Considerazioni sull'hardware aggiuntivo

Gli agenti di test generano una quantità notevole di dati sui controller di test, a seconda della durata e della dimensione del test. In genere, è necessario pianificare altri 10 GB di spazio di archiviazione su disco rigido ogni 24 ore di dati di test.

Oltre ai requisiti hardware consigliati, considerare la possibilità di impiegare hardware aggiuntivo per i server importanti, ad esempio alimentatori e ventole ridondanti.

### <a name="language-requirements"></a>Requisiti delle lingue

Per evitare confusione e semplificare le operazioni, è consigliabile configurare il test controller e gli agenti di test in modo che usino la stessa lingua del sistema operativo del computer e di Team Foundation Server. Se l'agente di test e il controller di test sono installati su computer diversi, devono essere configurati per utilizzare la stessa lingua. È possibile, tuttavia, installare una versione di Visual Studio in un'altra lingua in un sistema operativo in lingua inglese, a condizione che questa lingua corrisponda a quella della distribuzione di Team Foundation Server.

## <a name="monitor-agent-resources"></a>Monitorare le risorse dell'agente

È possibile monitorare i computer dell'agente per determinarne le esigenze in termini di risorse osservando i processi di **QTAgent\*.exe** che vengono eseguiti e scalati durante i test. Il più frequente collo di bottiglia nei processi QTAgent*.exe è l'utilizzo della CPU. Se l'utilizzo della CPU è costantemente superiore al 90%, è un'indicazione che l'agente è sovraccarico. Un altro collo di bottiglia frequente è l'utilizzo memoria. Per i test complessi, il monitoraggio di queste risorse può aiutare a determinare se è necessario aumentare le risorse dei computer o distribuire i test in modo diverso.

## <a name="see-also"></a>Vedere anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)