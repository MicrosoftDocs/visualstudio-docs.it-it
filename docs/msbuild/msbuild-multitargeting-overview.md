---
title: Panoramica del multitargeting di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e85bb64252a73195e4ab8226cfbdb141199107d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-multitargeting-overview"></a>Cenni preliminari sul multitargeting di MSBuild
Tramite MSBuild è possibile compilare un'applicazione da eseguire in una qualunque delle tante versioni di .NET Framework e in una qualunque delle tante piattaforme di sistema. Ad esempio, è possibile compilare un'applicazione da eseguire in .NET Framework 2.0 in una piattaforma a 32 bit e compilare la stessa applicazione da eseguire in .NET Framework 4.5 in una piattaforma a 64 bit.  
  
> [!IMPORTANT]
>  Nonostante il nome "multitargeting", un progetto può essere destinato a un solo framework e a una sola piattaforma per volta.  
  
 Di seguito sono riportate alcune delle funzionalità di definizione destinazione di MSBuild:  
  
-   È possibile sviluppare applicazioni destinate a una precedente versione di .NET Framework, ad esempio le versioni 2.0, 3.5 e 4.  
  
-   È possibile avere un framework di destinazione diverso da .NET Framework, ad esempio Silverlight.  
  
-   L'applicazione può essere destinata a un *profilo del framework*, vale a dire un subset predefinito di un framework di destinazione.  
  
-   In caso di rilascio di un Service Pack per la versione corrente di .NET Framework, è possibile destinare l'applicazione a esso.  
  
-   Il multitargeting di MSBuild garantisce che un'applicazione usi solo le funzionalità disponibili nel framework e nella piattaforma di destinazione.  
  
## <a name="target-framework-and-platform"></a>Framework e piattaforma di destinazione  
 Un *framework di destinazione* è la versione di .NET Framework per la quale un progetto è stato compilato appositamente e una *piattaforma di destinazione* è la piattaforma di sistema per la quale il progetto è stato compilato appositamente.  Ad esempio, è preferibile destinare un'applicazione a .NET Framework 2.0 per eseguirla su una piattaforma a 32 bit compatibile con la famiglia di processori 802x86 (x86). La combinazione di framework di destinazione e piattaforma di destinazione è nota come *contesto di destinazione*. Per altre informazioni, vedere [Framework e piattaforma di destinazione di MSBuild](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Set di strumenti (ToolsVersion)  
 Un set di strumenti comprende strumenti, attività e destinazioni usati per creare l'applicazione. Un set di strumenti include compilatori come csc.exe e vbc.exe, il file di destinazioni comuni (microsoft.common.targets) e il file delle attività comuni (microsoft.common.tasks). Il Set di strumenti 4.5 può essere usato per definire le destinazioni di .NET Framework versioni 2.0, 3.0, 3.5, 4 e 4.5. Tuttavia, il Set di strumenti 2.0 consente soltanto di scegliere come destinazione .NET Framework versione 2.0. Per altre informazioni, vedere [Set di strumenti di MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Assembly di riferimento  
 Gli assembly di riferimento specificati nel set di strumenti aiutano a progettare e sviluppare un'applicazione. Questi assembly di riferimento non solo consentono una specifica compilazione delle destinazioni, ma limitano anche i componenti e le funzionalità dell'IDE di Visual Studio a quelli compatibili con la destinazione. Per altre informazioni, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md)  
  
## <a name="configuring-targets-and-tasks"></a>Configurazione di destinazioni e attività  
 È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out-of-process con MSBuild, in modo che si possano scegliere come destinazione contesti notevolmente diversi da quello corrente.  Ad esempio, è possibile scegliere come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione .NET Framework 4.5 su una piattaforma a 64 bit. Per altre informazioni, vedere [Configurazione di destinazioni e attività](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Possono verificarsi errori se si tenta di fare riferimento a un assembly che non fa parte del contesto di destinazione. Per altre informazioni su questi errori e su come agire al riguardo, vedere [Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).