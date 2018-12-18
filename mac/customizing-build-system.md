---
title: Personalizzazione del sistema di compilazione
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 649289700aa984235f432528a59b970762d26be0
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-the-build-system"></a>Personalizzazione del sistema di compilazione

MSbuild è un motore di compilazione, sviluppato da Microsoft, che consente la compilazione di applicazioni, principalmente di applicazioni .NET. Anche il framework Mono ha una propria implementazione di Microsoft Build Engine, denominata **xbuild**. L'implementazione xbuild, tuttavia, è stata eliminata gradualmente a favore dell'uso di MSBuild in tutti i sistemi operativi.

**MSbuild** è il sistema principalmente usato per la compilazione dei progetti in Visual Studio per Mac. 

Il funzionamento di MSBuild si basa su un set di input, ad esempio file di origine, che vengono trasformati in output, ad esempio file eseguibili, tramite la chiamata a strumenti quali il compilatore. 


## <a name="msbuild-file"></a>File di MSBuild

MSBuild usa un file XML, denominato file di progetto, che definisce *elementi* che fanno parte del progetto (ad esempio risorse immagine) e *proprietà* necessarie per la compilazione del progetto stesso. Questo file di progetto ha sempre un'estensione terminante in `proj`, ad esempio `.csproj` per i progetti C#. 

### <a name="viewing-the-msbuild-file"></a>Visualizzazione del file di MSBuild

Per individuare il file MSBuild, fare clic con il pulsante destro del mouse sul nome del progetto e scegliere **Visualizza in Finder**. Nella finestra del Finder verranno visualizzati tutti i file e tutte le cartelle correlate al progetto, incluso il file `.csproj`, come illustrato nell'immagine seguente:

![](media/customizing-build-system-image1.png)

Per visualizzare il file `.csproj` in una nuova scheda in Visual Studio per Mac, fare clic con il pulsante destro del mouse sul nome del progetto e scegliere **Strumenti > Modifica file**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Composizione del file di MSBuild

Tutti i file di MSBuild contengono un elemento radice obbligatorio `Project`, come segue:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

In genere, il progetto importerà anche un file `.targets`. Questo file contiene molte delle regole che descrivono come elaborare e compilare i vari file. L'importazione viene di solito visualizzata verso la fine del file `proj` e per i progetti C# ha un aspetto simile al seguente:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Il file con estensione targets è un altro file di MSBuild. Questo file contiene codice di MSBuild riutilizzabile in altri progetti. Ad esempio, il file `Microsoft.CSharp.targets`, presente in una directory rappresentata dalla proprietà (o variabile) `MSBuildBinPath`, contiene la logica per la compilazione di assembly C# da file di origine C#.

### <a name="items-and-properties"></a>Elementi e proprietà

In MSBuild sono presenti due tipi di dati fondamentali: *elementi* e *proprietà*, illustrati in modo più dettagliato nelle sezioni seguenti.

#### <a name="properties"></a>Proprietà

Le proprietà sono coppie chiave/valore usate per memorizzare impostazioni che influiscono sulla compilazione, ad esempio le opzioni del compilatore.

Le proprietà vengono impostate tramite PropertyGroup. È possibile usare un numero qualsiasi di PropertiesGroup e questi possono contenere un numero qualsiasi di proprietà. 

Il codice XML del PropertyGroup per una semplice applicazione console, ad esempio, può essere simile al seguente:

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

Il frammento di codice seguente, ad esempio, crea le schermate di avvio di iOS. Le schermate di avvio hanno il tipo di compilazione `BundleResource`, con il percorso dell'immagine come specifica:

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


