---
title: Installare agenti di test e test controller per Visual Studio | Microsoft Docs
ms.date: 03/02/2018
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bc5790ef520e86bf853cee6086bd6c8739cc23a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="install-test-agents-and-test-controllers"></a>Installare agenti di test e test controller

Per gli scenari di test che usano Visual Studio e Visual Studio Team Services (VSTS) o Team Foundation Server (TFS), non occorre un test controller. Gli agenti per Visual Studio gestiscono l'orchestrazione mediante la comunicazione con VSTS o TFS. Uno scenario potrebbe essere l'esecuzione continuativa di test per i flussi di lavoro di compilazione e versione in VSTS o TFS.

Potrebbe anche essere utile valutare se è preferibile usare la [gestione di compilazione e versione](use-build-or-rm-instead-of-lab-management.md) anziché Lab Management.

## <a name="system-requirements"></a>Requisiti di sistema

| Elemento | Requisiti |
| ---- | ------------ |
| **Agente** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installare il test controller e gli agenti di test

È possibile scaricare gli agenti per Visual Studio 2017 da [visualstudio.com](https://www.visualstudio.com/downloads/?q=agents). Scorrere fino in fondo alla pagina e cercare *Agents per Visual Studio 2017*. Selezionare l'opzione *Agente* o *Controller* e quindi scegliere *Download*. Eseguire il file eseguibile scaricato per installare l'agente di test o il test controller.

È possibile scaricare gli agenti per Visual Studio 2015 e Visual Studio 2013 dalla pagina di [download precedente](https://www.visualstudio.com/vs/older-downloads/).

Questi programmi di installazione sono disponibili come file ISO per facilitarne l'installazione nelle macchine virtuali.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versioni compatibili di TFS, Microsoft Test Manager, test controller e agente di test

È possibile combinare diverse versioni di TFS, Microsoft Test Manager (MTM), test controller e agente di test come indicato nella tabella seguente:

| TFS | MTM con Centro lab | Controller | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2017 | 2017 | 2017 |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: aggiornamento dalla versione 2015 o nuova installazione | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: aggiornamento da 2013 | 2013 | 2013 |2013 |
| 2015: nuova installazione | 2013 | 2013 | 2013 |
| 2015: aggiornamento da 2013 o nuova installazione | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Eseguire l'aggiornamento da agenti di test di Visual Studio 2013

È consigliabile usare gli agenti per Visual Studio in tutti i nuovi scenari di test automatizzato. Per scaricare e installare gli agenti di test nel computer, è possibile usare l'attività *Deploy Test Agents* (Distribuisci agenti di test) in una definizione di compilazione.

La tabella seguente visualizza gli scenari supportati da Agents per Visual Studio 2013 e le alternative per Team Foundation Server (TFS) 2015 e VSTS:

| Scenari supportati da Agents per Visual Studio 2013 | Alternativa in TFS e VSTS |
| --- | --- |
| Flusso di lavoro compilazione, distribuzione e test in Visual Studio | Gli utenti possono usare una [definizione di compilazione](/vsts/build-release/) (non una compilazione XAML) per gli scenari di compilazione, distribuzione e test in TFS. |
| Test di carico (test delle prestazioni) usando computer remoti in posizioni locali | Per eseguire i test di carico in locale, usare Test Controller e Test Agents 2013 Update 5. |
| Esecuzione remota di test automatizzati da Microsoft Test Manager usando un ambiente lab | Attualmente non è disponibile nessuna alternativa per questo scenario. È consigliabile usare l'attività Esegui test funzionali nelle definizioni di compilazione e di versione (non in una compilazione XAML) per eseguire i test in modalità remota. |
| Sviluppatori che eseguono test remoti in Visual Studio | Non è più supportato. |
