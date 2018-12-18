---
title: Personalizzazione del sistema di compilazione | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 2d17a952c58e5ef7e593ee7aeb1980e09a376800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-build-system"></a>Personalizzazione del sistema di compilazione

MSbuild è un motore di compilazione, sviluppato da Microsoft, che consente la compilazione di applicazioni, principalmente di applicazioni .NET. Anche il framework Mono ha una propria implementazione di Microsoft Build Engine, denominata **xbuild**. L'implementazione xbuild, tuttavia, è stata eliminata gradualmente a favore dell'uso di MSBuild in tutti i sistemi operativi.

**MSbuild** è il sistema principalmente usato per la compilazione dei progetti in Visual Studio per Mac. 

Il funzionamento di MSBuild si basa su una serie di input, ad esempio file di origine, che vengono trasformati in output, ad esempio file eseguibili, tramite la chiamata a strumenti quali il compilatore. 


## <a name="msbuild-file"></a>File di MSBuild

MSBuild usa un file XML, denominato file di progetto, che definisce *elementi* che fanno parte del progetto (ad esempio risorse immagine) e *proprietà* necessarie per la compilazione del progetto stesso. Questo file di progetto ha sempre un'estensione terminante in `proj`, ad esempio `.csproj` per i progetti C#. 

### <a name="viewing-the-msbuild-file"></a>Visualizzazione del file di MSBuild
Per individuare questo file, è possibile fare clic con il pulsante destro del mouse sul nome del progetto e selezionare **Mostra nel Finder**. Verranno visualizzati tutti i file e tutte le cartelle correlate al progetto, incluso il file `.csproj`, come illustrato di seguito:

![](media/customizing-build-system-image1.png)

È anche possibile visualizzare il file `.csproj` in una nuova scheda in Visual Studio per Mac facendo clic con il pulsante destro del mouse sul nome del progetto e scegliendo **Strumenti > Modifica file**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Composizione del file di MSBuild

Tutti i file di MSBuild contengono un elemento radice obbligatorio `Project`, come visualizzato di seguito:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

In genere, il progetto importa anche un file `.targets`, che contiene molte delle regole che descrivono come elaborare e compilare i vari file. Questa parte, di solito visualizzata verso la fine del file `proj`, per i progetti C# ha un aspetto simile al seguente:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Il file con estensione targets è un altro file di MSBuild. Questo file contiene codice di MSBuild riutilizzabile in altri progetti. Ad esempio, il file `Microsoft.CSharp.targets`, presente in una directory rappresentata dalla proprietà (o variabile) `MSBuildBinPath`, contiene la logica per la compilazione di assembly C# da file di origine C#.

### <a name="items-and-properties"></a>Elementi e proprietà

In MSBuild sono presenti due tipi di dati fondamentali: *elementi* e *proprietà*, illustrati in modo più dettagliato di seguito.

#### <a name="properties"></a>Proprietà

Le proprietà sono coppie chiave/valore usate per memorizzare impostazioni che influiscono sulla compilazione, ad esempio le opzioni del compilatore.

Le proprietà vengono impostate tramite PropertyGroup. È possibile usare un numero qualsiasi di PropertiesGroup e questi possono contenere un numero qualsiasi di proprietà. 

Il codice di un PropertyGroup per una semplice applicazione console, ad esempio, può essere simile al seguente:

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

È possibile fare riferimento alle proprietà da espressioni che usano la sintassi `$()`. L'espressione `$(Foo)`, ad esempio, verrà valutata come valore della proprietà `Foo`. Se la proprietà non è stata impostata, verrà valutata come stringa vuota, senza alcun errore.

#### <a name="items"></a>Elementi

Gli elementi consentono di gestire l'input nel sistema di compilazione sotto forma di elenchi o set e in genere rappresentano file. Ogni elemento ha un *tipo*, una *specifica*e *metadati* arbitrari facoltativi. Si noti che MSBuild non opera su elementi singoli, ma su tutti gli elementi di un tipo specifico, ovvero su un *set* di elementi.

Gli elementi vengono creati tramite la dichiarazione di un `ItemGroup`. Può esistere un numero qualsiasi di ItemGroup, e questi possono contenere un numero qualsiasi di elementi. 

Il frammento di codice seguente, ad esempio, crea le schermate di avvio di iOS. Queste sono di tipo `BundleResource`, con il percorso dell'immagine come specifica:

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 È possibile fare riferimento agli elementi da espressioni che usano la sintassi `@()`. Ad esempio, `@(BundleResource)` verrà valutato come set di elementi BundleResource, ovvero tutti gli elementi BundleResource. Se non sono presenti elementi di questo tipo, l'espressione sarà vuota, senza alcun errore.

## <a name="resources-for-learning-msbuild"></a>Risorse di approfondimento di MSBuild

Per approfondire le proprie conoscenze di MSBuild, è possibile usare le risorse seguenti:

* [MSDN: panoramica](https://msdn.microsoft.com/library/dd393574.aspx)
* [MSDN: concetti](https://msdn.microsoft.com/library/dd637714.aspx)


