---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Professional 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/01/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: 5719032b-2c2e-416e-a281-a4573ec74e38
ms.workload: multiple
ms.openlocfilehash: 4f53afd1b91464823e506d26bf86a443ad572329
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-professional-2017-component-directory"></a>Elenco dei componenti di Visual Studio Professional 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando o che è possibile specificare come dipendenza in un manifesto VSIX. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. * È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Quando si impostano le dipendenze nel manifesto VSIX, è necessario specificare solo gli ID dei componenti. Usare le tabelle in questa pagina per determinare le dipendenze minime dei componenti. In alcuni scenari, ciò potrebbe portare alla specifica di un solo componente da un carico di lavoro. In altri scenari è possibile che vengano specificati più componenti da un singolo carico di lavoro o più componenti da più carichi di lavoro. Per altre informazioni, vedere la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).


Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Pagina iniziale di Visual Studio per utenti di C++ | 15.0.27128.1 | Facoltativo

## <a name="azure-development"></a>Sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrizione:** Azure SDK, strumenti e progetti per lo sviluppo di app cloud e la creazione di risorse.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Obbligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per processi Web di Microsoft Azure | 15.0.27128.1 | Obbligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obbligatorio
Microsoft.Component.NetFX.Core.Runtime | Runtime di .NET Core | 15.0.26208.0 | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Obbligatorio
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27019.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 15.0.26823.1 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prerequisiti per lo sviluppo per Azure | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per processi Web di Microsoft Azure | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.0.26504.0 | Consigliato
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Strumenti di base di Azure Resource Manager | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Strumenti di Service Fabric | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Strumenti di Servizi cloud di Azure | 15.0.26504.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Strumenti di Azure Resource Manager | 15.0.27005.2 | Consigliato
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.0.27128.1 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.0.27019.1 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.0.27005.2 | Facoltativo
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0-1.1 per desktop | 15.0.26919.1 | Facoltativo
Microsoft.NetCore.1x.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0-1.1 per il Web | 15.0.26919.1 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy di Archiviazione di Azure | 15.0.26906.1 | Facoltativo
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell Tools | 3.0.552 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.27005.2 | Facoltativo

## <a name="data-storage-and-processing"></a>Archiviazione ed elaborazione dei dati

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrizione:** consente di connettere, sviluppare e testare soluzioni dati con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Consigliato
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.4.2.1439 | Consigliato
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Consigliato
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 15.0.27005.2 | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 15.0.27102.0 | Facoltativo

## <a name="data-science-and-analytical-applications"></a>Applicazioni analitiche e di analisi scientifica dei dati

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrizione:** linguaggi e strumenti per la creazione di applicazioni di analisi scientifica dei dati, tra cui Python, R e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 a 64 bit (5.0.0) | 5.0.0 | Consigliato
Microsoft.Component.CookiecutterTools | Supporto modello Cookiecutter | 15.0.26621.2 | Consigliato
Microsoft.Component.PythonTools | Supporto linguaggio Python | 15.0.26823.1 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 15.0.27005.2 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.27019.1 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Consigliato
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 15.0.27102.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.RHost | Supporto runtime per strumenti di sviluppo R | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.RTools | Supporto linguaggio R | 15.0.26919.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Component.Anaconda2.x64 | Anaconda2 a 64 bit (5.0.0) | 5.0.0 | Facoltativo
Component.Anaconda2.x86 | Anaconda2 a 32 bit (5.0.0) | 5.0.0 | Facoltativo
Component.Anaconda3.x86 | Anaconda3 a 32 bit (5.0.0) | 5.0.0 | Facoltativo
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Facoltativo

## <a name="net-desktop-development"></a>Sviluppo per desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrizione:** consente di compilare applicazioni WPF, Windows Form e console con C#, Visual Basic e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 15.0.27102.0 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Obbligatorio
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 15.0.27005.2 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 15.0.26208.0 | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.0.27128.1 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.0.27019.1 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.0.27005.2 | Facoltativo
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Facoltativo
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0-1.1 per desktop | 15.0.26919.1 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 15.0.27102.0 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Facoltativo
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Facoltativo

## <a name="game-development-with-unity"></a>Sviluppo di giochi con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrizione:** consente di creare giochi 2D e 3D con Unity, un potente ambiente di sviluppo multipiattaforma.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools per Unity | 15.0.27005.2 | Obbligatorio
Component.UnityEngine.x64 | Editor di Unity 2017.2 a 64 bit | 15.0.27128.1 | Consigliato
Component.UnityEngine.x86 | Editor di Unity 5.6 a 32 bit | 15.0.27102.0 | Consigliato

## <a name="linux-development-with-c"></a>Sviluppo di applicazioni Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrizione:** consente di creare ed eseguire il debug di applicazioni eseguite in un ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.0.26621.2 | Obbligatorio
Component.Linux.CMake | Strumenti Visual C++ per CMake e Linux | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Component.MDD.Linux | Visual C++ for Linux Development | 15.0.27005.2 | Facoltativo
Component.MDD.Linux.GCC.arm | Sviluppo incorporato e IoT | 15.0.27102.0 | Facoltativo

## <a name="desktop-development-with-c"></a>Sviluppo di applicazioni desktop con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrizione:** consente di compilare applicazioni di Windows classiche usando tutta la potenza del set di strumenti Microsoft C++ e ATL, oltre a funzionalità facoltative quali MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di Visual C++ 2017 Redistributable | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di Visual C++ | 15.0.27102.0 | Obbligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti Visual C++ per CMake | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adattatore di test per Boost.Test | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 15.0.27102.0 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 15.0.27019.1 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (sperimentale) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli per la libreria standard (sperimentale) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.WinXP | Supporto Windows XP per C++ | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Supporto Windows XP per C++ | 15.0.27019.1 | Facoltativo

## <a name="game-development-with-c"></a>Sviluppo di giochi con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrizione:** consente di sfruttare tutte le funzionalità di C++ per compilare giochi professionali basati su DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di Visual C++ 2017 Redistributable | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Consigliato
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Facoltativo
Component.Android.SDK23.Private | Programma di installazione di Android SDK (livello API 23) (installazione locale) | 15.0.27128.1 | Facoltativo
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Facoltativo
Component.Cocos | Cocos | 15.0.26906.1 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 15.0.27019.1 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Facoltativo
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Facoltativo
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 15.0.26606.0 | Facoltativo
Component.Unreal | Programma di installazione di Unreal Engine | 15.0.26621.2 | Facoltativo
Component.Unreal.Android | Supporto Visual Studio Android per Unreal Engine | 15.0.27005.2 | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Facoltativo
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | 15.0.27019.1 | Facoltativo

## <a name="mobile-development-with-c"></a>Sviluppo di app per dispositivi mobili con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Obbligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Consigliato
Component.Android.SDK19 | Programma di installazione di Android SDK (livelli API 19 e 21) | 15.0.27128.1 | Consigliato
Component.Android.SDK22 | Programma di installazione di Android SDK (livello API 22) | 15.0.27128.1 | Consigliato
Component.Android.SDK25 | Programma di installazione di Android SDK (livello API 25) | 15.0.27128.1 | Consigliato
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Consigliato
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 15.0.26606.0 | Consigliato
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Facoltativo
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (a 32 bit) | 12.1.10 | Facoltativo
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (a 32 bit) | 13.1.7 | Facoltativo
Component.Android.SDK23 | Programma di installazione di Android SDK (livello API 23) (installazione globale) | 15.0.27128.1 | Facoltativo
Component.Google.Android.Emulator.API23.V2 | Emulatore Google Android (livello API 23) (installazione globale) | 15.0.27128.1 | Facoltativo
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (installazione globale) | 15.0.27128.1 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 15.0.27019.1 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Facoltativo
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Facoltativo
Component.MDD.IOS | Strumenti di sviluppo per app iOS in C++ | 15.0.26621.2 | Facoltativo

## <a name="net-core-cross-platform-development"></a>Sviluppo multipiattaforma .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrizione:** consente di creare applicazioni multipiattaforma con .NET Core, ASP.NET Core, HTML/JavaScript e contenitori con il supporto di Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27019.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Consigliato
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0-1.1 per desktop | 15.0.26919.1 | Facoltativo
Microsoft.NetCore.1x.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0-1.1 per il Web | 15.0.26919.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 15.0.26720.2 | Facoltativo

## <a name="mobile-development-with-net"></a>Sviluppo di applicazioni per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Obbligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27019.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motore di creazione modello ASP.NET | 15.0.27102.0 | Obbligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Consigliato
Component.Android.SDK25 | Programma di installazione di Android SDK (livello API 25) | 15.0.27128.1 | Consigliato
Component.Google.Android.Emulator.API25 | Emulatore Google Android (API livello 25) | 15.0.27128.1 | Consigliato
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (installazione globale) | 15.0.27128.1 | Consigliato
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Consigliato
Component.Xamarin | Xamarin | 15.0.27009.1 | Consigliato
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Consigliato
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.0.27005.2 | Consigliato
Component.Xamarin.SdkManager | Xamarin SDK Manager | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Merq | Strumenti interni comuni Xamarin | 15.0.26720.2 | Consigliato
Microsoft.VisualStudio.Component.MonoDebugger | Debugger di Mono | 15.0.26720.2 | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Facoltativo
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin | 15.0.27005.2 | Facoltativo

## <a name="aspnet-and-web-development"></a>Sviluppo ASP.NET e Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrizione:** consente di creare applicazioni Web con ASP.NET, ASP.NET Core, HTML/JavaScript e contenitori con il supporto di Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obbligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27019.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 2.0 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Consigliato
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 15.0.26823.1 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 15.0.27128.1 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.0.27128.1 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.0.27019.1 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.0.27005.2 | Facoltativo
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0-1.1 per desktop | 15.0.26919.1 | Facoltativo
Microsoft.NetCore.1x.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0-1.1 per il Web | 15.0.26919.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 15.0.26720.2 | Facoltativo
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.0.26606.0 | Facoltativo

## <a name="nodejs-development"></a>Sviluppo Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.Node.Tools | Supporto per Node.js | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Facoltativo

## <a name="officesharepoint-development"></a>Sviluppo per Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrizione:** consente di creare componenti aggiuntivi per Office e SharePoint, soluzioni SharePoint e componenti aggiuntivi VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Obbligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 15.0.27102.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools per Visual Studio | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools per Office (VSTO) | 15.0.26606.0 | Consigliato

## <a name="python-development"></a>Sviluppo Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrizione:** modifica, debug, sviluppo interattivo e controllo del codice per Python.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.CPython3.x64 | Python 3 a 64 bit (3.6.3) | 3.6.3.1 | Consigliato
Microsoft.Component.CookiecutterTools | Supporto modello Cookiecutter | 15.0.26621.2 | Consigliato
Microsoft.Component.PythonTools | Supporto linguaggio Python | 15.0.26823.1 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 15.0.27005.2 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 1.10.50912.1 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Component.Anaconda2.x64 | Anaconda2 a 64 bit (5.0.0) | 5.0.0 | Facoltativo
Component.Anaconda2.x86 | Anaconda2 a 32 bit (5.0.0) | 5.0.0 | Facoltativo
Component.Anaconda3.x64 | Anaconda3 a 64 bit (5.0.0) | 5.0.0 | Facoltativo
Component.Anaconda3.x86 | Anaconda3 a 32 bit (5.0.0) | 5.0.0 | Facoltativo
Component.CPython2.x64 | Python 2 a 64 bit (2.7.14) | 2.7.14 | Facoltativo
Component.CPython2.x86 | Python 2 a 32 bit (2.7.14) | 2.7.14 | Facoltativo
Component.CPython3.x86 | Python 3 a 32 bit (3.6.3) | 3.6.3.1 | Facoltativo
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 15.0.26720.2 | Facoltativo
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Facoltativo
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Facoltativo
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Facoltativo
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Facoltativo
Microsoft.Component.PythonTools.UWP | Supporto Python IoT | 15.0.26606.0 | Facoltativo
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 15.0.27005.2 | Facoltativo
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Facoltativo
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.0.26919.1 | Facoltativo
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Web | Strumenti di sviluppo ASP.NET e Web | 15.0.27005.2 | Facoltativo

## <a name="universal-windows-platform-development"></a>Sviluppo della piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrizione:** consente di creare applicazioni per la piattaforma UWP (Universal Windows Platform) con C#, VB, JavaScript o facoltativamente C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Obbligatorio
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obbligatorio
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 15.0.27005.2 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.UWP.Support | Strumenti della piattaforma UWP (Universal Windows Platform) | 15.0.26906.1 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Strumenti della piattaforma UWP (Universal Windows Platform) per Cordova | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native e .NET Standard | 15.0.27102.0 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulatore di Windows 10 Mobile (Creators Update) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ | 15.0.27019.1 | Facoltativo

## <a name="visual-studio-extension-development"></a>Sviluppo di estensioni di Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrizione:** consente di creare componenti aggiuntivi ed estensioni per Visual Studio, inclusi nuovi comandi, analizzatori del codice e finestre degli strumenti.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prerequisiti per lo sviluppo di estensioni di Visual Studio | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Facoltativo
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 15.0.27128.1 | Facoltativo
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Facoltativo
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | 15.0.27019.1 | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | 15.0.26823.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26606.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.0.26919.1 | Facoltativo

## <a name="mobile-development-with-javascript"></a>Sviluppo di app per dispositivi mobili con JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descrizione:** consente di creare app Android, iOS e della piattaforma UWP con Strumenti per Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Set di strumenti di Cordova 6.3.1 | 15.0.26504.0 | Obbligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.Cordova | Sviluppo di app per dispositivi mobili con funzionalità di base di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem and Shared Tooling | 15.0.26606.0 | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.0.27005.2 | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.0.27019.1 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Obbligatorio
Component.Android.SDK23.Private | Programma di installazione di Android SDK (livello API 23) (installazione locale) | 15.0.27128.1 | Facoltativo
Component.Google.Android.Emulator.API23.Private | Emulatore Google Android (livello API 23) (installazione locale) | 15.0.27128.1 | Facoltativo
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (installazione locale) | 15.0.27128.1 | Facoltativo
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Facoltativo
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.0.27019.1 | Facoltativo
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 15.0.27005.2 | Facoltativo
Microsoft.VisualStudio.Component.Git | GIT per Windows | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 15.0.26621.2 | Facoltativo
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulatore di Windows 10 Mobile (Creators Update) | 15.0.27019.1 | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.0.27128.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Strumenti della piattaforma UWP (Universal Windows Platform) per Cordova | 15.0.27005.2 | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
Component.Android.Emulator | Emulatore di Visual Studio per Android | 15.0.27128.1
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.13
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bit) | 11.3.15
Component.GitHub.VisualStudio | Estensione GitHub per Visual Studio | 2.2.0.10
Microsoft.Component.Blend.SDK.WPF | Blend for Visual Studio SDK per .NET | 15.0.27005.2
Microsoft.Component.HelpViewer | Help Viewer | 15.0.27005.2
Microsoft.VisualStudio.Component.DependencyValidation.Community | Convalida delle dipendenze | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2
Microsoft.VisualStudio.Component.LinqToSql | Strumenti di LINQ to SQL | 15.0.26208.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulatore Windows 10 Mobile (Anniversary Edition) | 15.0.27019.1
Microsoft.VisualStudio.Component.TestTools.Core | Funzionalità di base degli strumenti di test | 15.0.26606.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.0.26504.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26504.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Set di strumenti di VC++ 2017 versione 14.11 di Visual Studio 15.4 | 15.0.27128.1
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilatori e librerie di Visual C++ per ARM64 | 15.0.27019.1
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) per desktop C++ [ARM e ARM64] | 15.0.27128.1

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
