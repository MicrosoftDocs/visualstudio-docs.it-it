---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Desktop Express 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 03/05/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology:
- vs-acquisition
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.workload:
- multiple
ms.openlocfilehash: 651b2901c87e99d19c86edfe81e1767d64674a25
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="visual-studio-desktop-express-2017-workload-and-component-ids"></a>ID dei carichi di lavoro e dei componenti di Visual Studio Desktop Express 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando o che è possibile specificare come dipendenza in un manifesto VSIX. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Quando si impostano le dipendenze nel manifesto VSIX, è necessario specificare solo gli ID dei componenti. Usare le tabelle in questa pagina per determinare le dipendenze minime dei componenti. In alcuni scenari, ciò potrebbe portare alla specifica di un solo componente da un carico di lavoro. In altri scenari è possibile che vengano specificati più componenti da un singolo carico di lavoro o più componenti da più carichi di lavoro. Per altre informazioni, vedere la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express per Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Descrizione:** sviluppare applicazioni native e gestite come WPF, WinForms e Win32 con funzionalità di modifica del codice con riconoscimento della sintassi, controllo del codice sorgente e gestione degli elementi di lavoro. Include il supporto per C#, Visual Basic e Visual C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27205.0 | Obbligatorio
Microsoft.Component.HelpViewer | Help Viewer | 15.6.27323.2 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.6.27309.0 | Obbligatorio
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Obbligatorio
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27205.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilatori e librerie di Visual C++ per ARM64 | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) per desktop C++ [ARM e ARM64] | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.6.27406.0 | Obbligatorio

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
N/D | N/D | N/D

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
