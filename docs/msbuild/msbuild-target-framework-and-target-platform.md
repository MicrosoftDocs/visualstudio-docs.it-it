---
title: Framework e piattaforma di destinazione di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93eff2375e9b1cab043a30acaf5ebec31ba8e89f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-target-framework-and-target-platform"></a>Framework e piattaforma di destinazione di MSBuild
È possibile compilare un progetto per eseguirlo in un *framework di destinazione*, che è una versione particolare di .NET Framework e una *piattaforma di destinazione*, che è un'architettura software particolare.  Ad esempio, è possibile impostare un'applicazione come destinazione per eseguirla in .NET Framework 2.0 su una piattaforma a 32 bit compatibile con la famiglia di processori 802x86 ("x86"). La combinazione del framework e della piattaforma di destinazione è nota come *contesto di destinazione*.  
  
## <a name="target-framework-and-profile"></a>Profilo e framework di destinazione  
 Un framework di destinazione è una versione particolare di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in cui il proprio progetto è compilato per essere eseguito. La specifica di un framework di destinazione è necessaria perché abilita le funzionalità del compilatore e i riferimenti dell'assembly che sono esclusivi di quella versione di framework.  
  
 Le versioni seguenti di .NET Framework sono attualmente disponibili per l'uso:  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (incluso in Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (incluso in [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (incluso in [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (incluso in [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  
  
 Le versioni di .NET Framework sono diverse l'una dall'altra nell'elenco di assembly che ognuna rende disponibile come riferimento. Ad esempio, non è possibile compilare applicazioni WPF (Windows Presentation Foundation) a meno che il progetto non imposti .NET Framework versione 3.0 o versioni superiori come destinazione.  
  
 Il framework di destinazione viene specificato nella proprietà `TargetFrameworkVersion` nel file di progetto. È possibile modificare il framework di destinazione per un progetto usando le pagine di proprietà del progetto nell'ambiente di sviluppo integrato (IDE) di Visual Studio. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). I valori disponibili per `TargetFrameworkVersion` sono `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v.4.6.1`, `v4.6.2`, `4.7` e `4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 Un *profilo target* è un subset di un framework di destinazione. Ad esempio, Framework 4 Client Profile non include riferimenti agli assembly di MSBuild.  
  
 Il framework di destinazione viene specificato nella proprietà `TargetFrameworkProfile` in un file di progetto. È possibile modificare il profilo target usando il controllo del framework di destinazione nelle pagine delle proprietà del progetto nell'IDE. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Target Platform  
 Una *piattaforma* è una combinazione di hardware e software che definisce un particolare ambiente di runtime. Ad esempio,  
  
-   `x86` definisce un sistema operativo Windows a 32 bit che è in esecuzione su un processore 80x86 Intel o un suo equivalente.  

-   `x64` definisce un sistema operativo Windows a 64 bit che è in esecuzione su un processore x64 Intel o un suo equivalente.
  
-   `Xbox` definisce la piattaforma Microsoft Xbox 360.  
  
 Una *piattaforma di destinazione* è una particolare piattaforma in cui il proprio progetto è compilato per l'esecuzione. Il framework di destinazione viene specificato nella proprietà di compilazione `PlatformTarget` in un file di progetto. È possibile modificare la piattaforma di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione** nell'IDE.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  
  
```  
  
 Una *configurazione di destinazione* è un subset di una piattaforma di destinazione. Ad esempio, la configurazione `x86``Debug` non include la maggior parte delle ottimizzazioni di codice. La configurazione di destinazione viene specificata nella proprietà di compilazione `Configuration` in un file di progetto. È possibile modificare la configurazione di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione**.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)