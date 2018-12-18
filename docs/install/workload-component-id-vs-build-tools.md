---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti di Visual Studio per creare applicazioni basate su Windows classiche
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
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 415ad88d9ef51a5002c7e64dcd4abf76f97167c3
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Elenco dei componenti di Visual Studio Build Tools 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative a questa pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>Strumenti MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descrizione:** fornisce gli strumenti necessari per creare applicazioni basate su MSBuild.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.CoreBuildTools | Funzionalità di base di Visual Studio Build Tools | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# (compilatore) | 15.6.27406.0 | Facoltativo

## <a name="net-core-build-tools"></a>Strumenti di compilazione .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Descrizione:** strumenti per la compilazione di applicazioni .NET Core.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facoltativo

## <a name="nodejs-build-tools"></a>Strumenti di compilazione Node.js

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Supporto per Node.js | 15.6.27406.0 | Obbligatorio

## <a name="visual-c-build-tools"></a>Strumenti di compilazione Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Descrizione:** Consente di compilare applicazioni desktop di Windows usando il set di strumenti Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Funzionalità di base per Visual C++ Build Tools | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di Visual C++ 2017 Redistributable | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti Visual C++ per CMake | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 15.0.27005.2 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (sperimentale) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli per la libreria standard (sperimentale) | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilatori e librerie di Visual C++ per ARM64 | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) per desktop C++ [x86 e x64] | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C++ | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) per desktop C++ [ARM e ARM64] | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.WinXP | Supporto Windows XP per C++ | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Supporto Windows XP per C++ | 15.6.27406.0 | Facoltativo

## <a name="web-development-build-tools"></a>Strumenti di compilazione sviluppo Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descrizione:** attività e destinazioni di MSBuild per compilare applicazioni Web.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo WCF | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo Web | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Consigliato
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 15.6.27428.1 | Consigliato
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27406.0 | Consigliato
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.6.27406.0 | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Set di strumenti di VC++ 2017 versione 14.11 di Visual Studio 15.4 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Set di strumenti di VC++ 2017 versione 14.12 di Visual Studio 15.5 | 15.0.27406.0

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
