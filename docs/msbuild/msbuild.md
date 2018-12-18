---
title: MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26646ecef952a6f4ff761f4e7239fc6e7e920ea1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] è una piattaforma per la compilazione di applicazioni. Questo motore, anche noto come MSBuild, fornisce un XML Schema per un file di progetto che controlla il modo in cui la piattaforma di compilazione elabora e compila il software. Visual Studio utilizza MSBuild, ma esso non dipende da Visual Studio. Richiamando msbuild.exe nel progetto o nel file della soluzione, è possibile orchestrare e compilare prodotti in ambienti in cui Visual Studio non è installato.  
  
 Visual Studio utilizza MSBuild per caricare e compilare progetti gestiti. I file di progetto in Visual Studio (con estensione CSPROJ, VBPROJ, VCXPROJ e altre) contengono il codice XML di MSBuild che viene eseguito quando si compila un progetto usando l'IDE. I progetti di Visual Studio importano tutte le impostazioni e tutti i processi di compilazione necessari per eseguire il normale lavoro di sviluppo standard, ma è possibile estenderli o modificarli in Visual Studio o mediante un editor XML.  
  
 Per informazioni su MSBuild per C++, vedere [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).  
  
 Negli esempi seguenti viene illustrato quando è possibile eseguire le compilazioni tramite la riga di comando di MSBuild, anziché l'IDE di Visual Studio.  
  
-   Visual Studio non è installato.  
  
-   Si desidera usare la versione a 64 bit di MSBuild. Questa versione di MSBuild non è solitamente necessaria, ma consente l'accesso di MSBuild a una maggiore quantità di memoria.  
  
-   Si desidera eseguire una compilazione in più processi. Tuttavia, è possibile usare l'IDE per ottenere lo stesso risultato nei progetti di C++ e C#.  
  
-   Si intende modificare il sistema di compilazione. Ad esempio, può essere necessario consentire le azioni seguenti:  
  
    -   Pre-elabora i file prima che arrivino al compilatore.  
  
    -   Copiare gli output di compilazione in un'altra posizione.  
  
    -   Creare file compressi dagli output di compilazione.  
  
    -   Eseguire un passaggio di post-elaborazione. Ad esempio, può essere utile contrassegnare un assembly con una versione diversa.  
  
 È possibile scrivere codice nell'IDE di Visual Studio ed eseguire le compilazioni tramite MSBuild. In alternativa, è possibile compilare il codice nell'IDE in un computer di sviluppo e usare una riga di comando di MSBuild per compilare il codice integrato da più sviluppatori.  
  
> [!NOTE]
>  È possibile usare Team Foundation Build per compilare, testare e distribuire l'applicazione automaticamente. Il sistema di compilazione può eseguire le compilazioni automaticamente quando gli sviluppatori archiviano il codice, ad esempio come parte di una strategia di integrazione continuata, o secondo a una pianificazione, ad esempio una compilazione notturna di test di verifica compilazione. In Team Foundation Build il codice viene compilato tramite MSBuild. Per altre informazioni, vedere [Compilazione e versione](/vsts/build-release/index).  
  
 Nel presente argomento viene fornita una panoramica di MSBuild. Per un'esercitazione introduttiva, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **Contenuto dell'argomento**  
  
-   [Uso di MSBuild al prompt dei comandi](#BKMK_CommandPrompt)  
  
-   [File di progetto](#BKMK_ProjectFile)  
  
    -   [Proprietà](#BKMK_Properties)  
  
    -   [Elementi](#BKMK_Items)  
  
    -   [Attività](#BKMK_Tasks)  
  
    -   [Destinazioni](#BKMK_Targets)  
  
-   [Log di compilazione](#BKMK_BuildLogs)  
  
-   [Uso di MSBuild in Visual Studio](#BKMK_VisualStudio)  
  
-   [Multitargeting](#BKMK_Multitargeting)  
  
##  <a name="BKMK_CommandPrompt"></a> Uso di MSBuild al prompt dei comandi  
 Per eseguire [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] al prompt dei comandi, passare un file di progetto a MSBuild.exe con le opzioni appropriate della riga di comando. Le opzioni della riga di comando consentono di impostare proprietà, eseguire destinazioni specifiche e impostare altre opzioni che controllano il processo di compilazione. Ad esempio, per compilare il file `MyProj.proj` con la proprietà `Configuration` impostata su `Debug` si utilizza la sintassi della riga di comando seguente.  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Per altre informazioni sulle opzioni della riga di comando di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
>  Prima di scaricare un progetto, determinare l'attendibilità del codice.  
  
##  <a name="BKMK_ProjectFile"></a> File di progetto  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa un formato di file di progetto basato su XML chiaro ed estensibile. Il formato del file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] consente agli sviluppatori di descrivere gli elementi da compilare nonché la relativa modalità di compilazione per sistemi operativi e configurazioni di vario tipo. Gli sviluppatori hanno inoltre la possibilità di creare regole di compilazione riutilizzabili che possono essere organizzate in file separati. Ciò consente di eseguire in modo coerente le compilazioni relative ai vari progetti del prodotto.  
  
 Nelle sezioni seguenti vengono descritti alcuni elementi di base del formato di file dei progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Per un'esercitazione su come creare un file di progetto di base, vedere [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
###  <a name="BKMK_Properties"></a> Proprietà  
 Le proprietà sono coppie di chiave/valore che possono essere usate per configurare le compilazioni. Per dichiarare le proprietà, è necessario creare un elemento con lo stesso nome della proprietà, come figlio di un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Tramite il codice seguente, ad esempio, viene creata una proprietà denominata `BuildDir` con un valore `Build`.  
  
```xml  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 È possibile definire una proprietà in modo condizionale aggiungendo un attributo `Condition` nell'elemento. Il contenuto degli elementi condizionali viene elaborato solo se la condizione risulta essere `true`. Nell'esempio seguente viene definito l'elemento `Configuration`, se non è stato ancora definito.  
  
```xml  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Nel file di progetto, per fare riferimento a una proprietà, si usa la sintassi $(*PropertyName*). È possibile, ad esempio, fare riferimento alle proprietà degli esempi precedenti usando `$(BuildDir)` e `$(Configuration)`.  
  
 Per altre informazioni sulle proprietà, vedere [Proprietà di MSBuild](../msbuild/msbuild-properties.md).  
  
###  <a name="BKMK_Items"></a> Elementi  
 Gli elementi sono input nel sistema di compilazione e, in genere, rappresentano i file. Gli elementi sono raggruppati in tipi di elemento, in base a nomi di elemento definiti dall'utente. Tali tipi di elemento possono essere usati come parametri per le attività, le quali a loro volta utilizzano i singoli elementi dei tipi per eseguire i passaggi del processo di compilazione.  
  
 Per dichiarare gli elementi nel file di progetto è necessario creare, come figlio di un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md), un elemento con lo stesso nome del tipo di elemento. Ad esempio, il codice seguente crea un tipo di elemento denominato `Compile` che include due file.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Nel file di progetto è possibile fare riferimento ai tipi di elementi usando la sintassi @(*ItemType*). Ad esempio, per fare riferimento al tipo di elemento dell'esempio si utilizza la sintassi `@(Compile)`.  
  
 In MSBuild, i nomi di elementi e attributi prevedono la distinzione tra maiuscole e minuscole. I nomi di proprietà, elementi e metadati, invece, non prevedono tale distinzione. Nell'esempio seguente viene creato il tipo di elemento `Compile`, `comPile` o con qualsiasi altra variazione di maiuscole o minuscole e viene assegnato a esso il valore "one.cs;two.cs".  
  
```xml  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Gli elementi possono essere dichiarati usando caratteri jolly e, negli scenari di compilazione più avanzati, possono contenere metadati aggiuntivi. Per altre informazioni sugli elementi, vedere [Elementi](../msbuild/msbuild-items.md).  
  
###  <a name="BKMK_Tasks"></a> Attività  
 Le attività sono unità di codice eseguibile usate dai progetti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per eseguire operazioni di compilazione. Ad esempio, un'attività potrebbe compilare file di input o eseguire uno strumento esterno. Le attività possono essere riutilizzate e condivise da sviluppatori diversi in progetti diversi.  
  
 La logica di esecuzione di un'attività viene scritta in codice gestito e ne viene eseguito il mapping a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usando l'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Per scrivere un'attività personalizzata, è sufficiente creare un tipo gestito che implementi l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni su come scrivere le attività, vedere [Scrittura di attività](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include attività comuni che è possibile modificare in base a requisiti specifici.  Alcuni esempi sono [Copy](../msbuild/copy-task.md) per eseguire la copia dei file, [MakeDir](../msbuild/makedir-task.md) per creare le directory e [Csc](../msbuild/csc-task.md) per compilare i file di codice sorgente di Visual C#. Per l'elenco delle attività disponibili e delle relative informazioni sull'uso, vedere [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md).  
  
 Per eseguire un'attività in un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] si crea, come elemento figlio di un elemento [Target](../msbuild/target-element-msbuild.md), un elemento con il nome dell'attività. In genere le attività accettano parametri che vengono passati come attributi dell'elemento. Sia le proprietà sia gli elementi di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] possono essere usati come parametri. Ad esempio, il codice seguente chiama l'attività [MakeDir](../msbuild/makedir-task.md) e le passa il valore della proprietà `BuildDir` dichiarata nell'esempio precedente.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Per altre informazioni sulle attività, vedere [Attività](../msbuild/msbuild-tasks.md).  
  
###  <a name="BKMK_Targets"></a> Destinazioni  
 Le destinazioni raggruppano le attività in un determinato ordine ed espongono le sezioni del file di progetto come punti di ingresso al processo di compilazione. Le destinazioni vengono spesso raggruppate in sezioni logiche per garantire una maggiore leggibilità e consentire l'espansione. La suddivisione delle istruzioni di compilazione in più destinazioni consente di chiamare una parte del processo di compilazione da altre destinazioni senza dover copiare la corrispondente sezione di codice in ognuna di esse. Ad esempio, se alcuni punti di ingresso al processo di compilazione richiedono la compilazione di riferimenti, è possibile creare una destinazione che compila riferimenti e quindi eseguire tale destinazione da ognuno dei suddetti punti di ingresso.  
  
 Per dichiarare una destinazione nel file di progetto si usa l'elemento [Target](../msbuild/target-element-msbuild.md). Il codice seguente crea ad esempio una destinazione denominata `Compile`, che a sua volta chiama l'attività [Csc](../msbuild/csc-task.md) con l'elenco di elementi dichiarato nell'esempio precedente.  
  
```xml  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Negli scenari più avanzati, è possibile usare le destinazioni per descrivere relazioni reciproche ed eseguire analisi delle dipendenze, così da poter ignorare intere sezioni del processo di compilazione per le destinazioni che risultano essere già aggiornate. Per altre informazioni sulle destinazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).  
  
##  <a name="BKMK_BuildLogs"></a> Log di compilazione  
 È possibile registrare errori di compilazione, avvisi e messaggi sulla console o in un altro dispositivo di output. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) e [Registrazione in MSBuild](../msbuild/logging-in-msbuild.md).  
  
##  <a name="BKMK_VisualStudio"></a> Uso di MSBuild in Visual Studio  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene usato il formato di file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per archiviare le informazioni di compilazione relative ai progetti gestiti. Le impostazioni di progetto aggiunte o modificate usando l'interfaccia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono riflesse nel file .*proj generato per ogni progetto. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizza un'istanza di hosting di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per compilare progetti gestiti. Ciò significa che è possibile compilare un progetto gestito in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o al prompt dei comandi, anche se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è installato, con risultati identici.  
  
 Per un'esercitazione sull'uso di MSBuild in Visual Studio, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
##  <a name="BKMK_Multitargeting"></a> Multitargeting  
 Tramite Visual Studio è possibile compilare un'applicazione da eseguire in una qualunque delle tante versioni di .NET Framework. Ad esempio, è possibile compilare un'applicazione da eseguire in .NET Framework 2.0 in una piattaforma a 32 bit e compilare la stessa applicazione da eseguire in .NET Framework 4.5 in una piattaforma a 64 bit. La possibilità di compilare in più framework è denominata multitargeting.  
  
 Di seguito sono riportati alcuni dei vantaggi del multitargeting:  
  
-   È possibile sviluppare applicazioni destinate a versioni di .NET Framework precedenti, ad esempio le versioni 2.0, 3.0 e 3.5.  
  
-   È possibile avere framework di destinazione diversi da .NET Framework, ad esempio Silverlight.  
  
-   L'applicazione può essere destinata a un *profilo del framework*, vale a dire un subset predefinito di un framework di destinazione.  
  
-   In caso di rilascio di un Service Pack per la versione corrente di .NET Framework, è possibile destinare l'applicazione a esso.  
  
-   Il multitargeting garantisce che un'applicazione utilizzi solo le funzionalità disponibili nel framework e nella piattaforma di destinazione.  
  
 Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo.|  
|[Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md)|Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'IDE di Visual Studio.|  
|[Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)|Presenta i quattro blocchi predefiniti di MSBuild: proprietà, elementi, destinazioni e attività.|  
|[Elementi](../msbuild/msbuild-items.md)|Descrive i concetti generali su cui si basa il formato di file di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e le interazioni fra le singole parti del formato.|  
|[Proprietà di MSBuild](../msbuild/msbuild-properties.md)|Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che possono essere usate per configurare le compilazioni|  
|[Destinazioni](../msbuild/msbuild-targets.md)|Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando.|  
|[Attività](../msbuild/msbuild-tasks.md)|Mostra come creare un'unità di codice eseguibile che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può usare per eseguire operazioni di compilazione atomiche.|  
|[Condizioni](../msbuild/msbuild-conditions.md)|Descrive come usare l'attributo `Condition` in un elemento MSBuild.|  
|[Advanced Concepts](../msbuild/msbuild-advanced-concepts.md) (Concetti avanzati)|Illustra la suddivisione in batch, l'esecuzione di trasformazioni, il multitargeting e altre tecniche avanzate.|  
|[Registrazione a MSBuild](../msbuild/logging-in-msbuild.md)|Descrive come registrare eventi, messaggi ed errori.|  
|[Risorse aggiuntive](../msbuild/additional-msbuild-resources.md)|Elenca risorse della community e di supporto che consentono di ottenere altre informazioni su MSBuild.|  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  
 Collegamenti ad argomenti che contengono informazioni di riferimento.  
  
 [Glossario](msbuild-glossary.md) Definisce i termini comuni di MSBuild.
