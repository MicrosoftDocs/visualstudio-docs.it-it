---
title: Installare e configurare agenti di test | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5caa566e15f7f3c4c69f8d33a6c7dd0eead38785
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="install-and-configure-test-agents"></a>Installare e configurare agenti di test

Per gli scenari di test che usano Visual Studio e Visual Studio Team Services o Team Foundation Server (TFS) non è necessario un controller di test, perché Agents for Microsoft Visual Studio gestisce Orchestration comunicando con Team Services o TFS. Un esempio è il caso in cui si eseguono test continui con i flussi di lavoro di build e release in Team Services o TFS.

Se è necessario che l'agente di test o il controller di test funzioni con TFS 2013, usare Agents per Microsoft Visual Studio 2013 Update 5 e configurare il controller di test.

Considerare anche se può risultare più facile [usare invece Build o Release Management](use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>Cosa è necessario?

**Dove è possibile ottenere il controller di test e gli agenti di test?**

* Se si eseguono test usando attività Build vNext e si vuole installare agenti da una directory locale: 

  * [Scaricare Agents per Microsoft Visual Studio 2015 RTM e Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Scaricare Agents per Microsoft Visual Studio 2017 e Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs). Scegliere **Tools for Visual Studio 2015** e quindi selezionare **Agents per Visual Studio 2015** nella barra di spostamento a sinistra.

* [Scaricare Agents per Microsoft Visual Studio 2013 Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264) se si vuole eseguire:

  * Test di carico usando computer remoti in posizioni locali.

  * Test continui in remoto con Microsoft Test Manager o MSTest e impostazioni test per ambienti lab.

  * Test continui con TFS 2013.

Questi programmi di installazione sono disponibili come file ISO (CD virtuali) per facilitarne l'installazione nelle macchine virtuali. 

[È possibile combinare versioni di TFS, di Microsoft Test Manager, del controller di test e dell'agente di test?](#MixedVersions)

**Quali sono i requisiti di sistema per l'installazione del controller di test e degli agenti di test?**

| Elemento | Requisiti |
| ---- | ------------ |
| **Agente** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Domande e risposte

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>D: È possibile combinare versioni di TFS, di Microsoft Test Manager, del controller di test e dell'agente di test?

R: Sì, le combinazioni compatibili e supportate sono elencate di seguito:

| TFS | Microsoft Test Manager con Lab Center | Controller | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: aggiornamento da 2013 | 2013 | 2013 |2013 |
| 2015: nuova installazione | 2013 | 2013 | 2013 |
| 2015: aggiornamento da 2013 o nuova installazione | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>D: Test Agent 2015 supporta tutti gli scenari supportati dal controller di test e dall'agente di test di Visual Studio 2013?

R: È consigliabile usare Agents per Visual Studio in tutti i nuovi scenari di test automatizzato. Per scaricare e installare gli agenti di test nel computer è possibile usare l'attività Deploy Test Agents (Distribuisci agenti di test) in una definizione di compilazione.
La tabella seguente visualizza gli scenari supportati da Agents per Visual Studio 2013 e le alternative per Team Foundation Server (TFS) 2015 e Team Services (TS).

| Scenari supportati da Agents per Visual Studio 2013 | Alternativa in TFS e TS |
| --- | --- |
| Flusso di lavoro compilazione, distribuzione e test in Visual Studio | Gli utenti possono usare una [definizione di compilazione](https://www.visualstudio.com/team-services/continuous-integration/) (non una compilazione XAML) per gli scenari di compilazione, distribuzione e test in TFS. |
| Test di carico (test delle prestazioni) usando computer remoti in posizioni locali | Per eseguire i test carico in locale usare Test Controller o Test Agent 2013 Update 5. [Altre informazioni](https://msdn.microsoft.com/library/ff400223.aspx). |
| Esecuzione remota di test automatizzati da Microsoft Test Manager usando un ambiente lab | Attualmente non è disponibile nessuna alternativa per questo scenario. È consigliabile usare l'attività Esegui test funzionali nelle definizioni di compilazione e di versione (non in una compilazione XAML) per eseguire i test in modalità remota. |
| Sviluppatori che eseguono test remoti in Visual Studio | Non è più supportato. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Vedere anche

* [Configurazione di computer e raccolta di informazioni diagnostiche tramite impostazioni test](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
