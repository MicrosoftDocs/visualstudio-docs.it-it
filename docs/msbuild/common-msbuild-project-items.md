---
title: Elementi di progetto MSBuild comuni | Microsoft Docs
description: Informazioni sugli elementi di progetto MSBuild comuni. Gli elementi sono denominati riferimenti a uno o più file e hanno metadati come nomi file, percorsi e numeri di versione.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceb6b01f06964b8c79fa7357da6688e2e0229799
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672826"
---
# <a name="common-msbuild-project-items"></a>Elementi di progetto MSBuild comuni

In MSBuild un elemento è un riferimento denominato a uno o più file. Gli elementi contengono metadati quali ad esempio nomi file, percorsi e numeri di versione. Tutti i tipi di progetto in Visual Studio hanno più elementi in comune. Questi elementi sono definiti nel file *Microsoft.Build.CommonTypes.xsd*.

Questo articolo elenca tutti gli elementi di progetto comuni.

## <a name="reference"></a>Informazioni di riferimento

Rappresenta un riferimento all'assembly (gestito) nel progetto.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|HintPath|Stringa facoltativa. Percorso relativo o assoluto dell'assembly.|
|Nome|Stringa facoltativa. Il nome visualizzato dell'assembly, ad esempio "System.Windows.Forms".|
|FusionName|Stringa facoltativa. Specifica il nome Fusion semplice o sicuro per l'elemento.<br /><br /> Questo attributo, se specificato, consente di risparmiare tempo in quanto non comporta l'apertura del file di assembly per ottenere il nome Fusion.|
|SpecificVersion|Valore booleano facoltativo. Specifica se è necessario fare riferimento solo alla versione nel nome Fusion.|
|Alias|Stringa facoltativa. Gli alias per il riferimento.|
|Privato|Valore booleano facoltativo. Specifica se il riferimento deve essere copiato nella cartella di output. Questo attributo corrisponde alla proprietà **Copia localmente** del riferimento nell'IDE di Visual Studio.|

## <a name="comreference"></a>COMReference

Rappresenta un riferimento a un oggetto COM (non gestito) nel progetto. Questo elemento si applica solo ai progetti .NET.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Nome|Stringa facoltativa. Nome visualizzato del componente|
|Guid|Stringa obbligatoria. GUID per il componente, nel formato {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Stringa obbligatoria. La parte principale del numero di versione del componente. Ad esempio, "5" se il numero di versione completo è "5.46".|
|VersionMinor|Stringa obbligatoria. La parte secondaria del numero di versione del componente. Ad esempio, "46" se il numero di versione completo è "5.46."|
|LCID|Stringa facoltativa. LocaleID per il componente.|
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|
|Isolato|Valore booleano facoltativo. Specifica se il componente è un componente reg-free.|

## <a name="comfilereference"></a>COMFileReference

Rappresenta un elenco di librerie di tipi passate al parametro `TypeLibFiles` della destinazione [ResolvedComreference](resolvecomreference-task.md). Questo elemento si applica solo ai progetti .NET.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|

## <a name="nativereference"></a>NativeReference

Rappresenta un file manifesto nativo o un riferimento a tale file.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Nome|Stringa obbligatoria. Il nome base del file manifesto.|
|HintPath|Stringa obbligatoria. Il percorso relativo del file manifesto.|

## <a name="projectreference"></a>ProjectReference

Rappresenta un riferimento a un altro progetto. `ProjectReference` gli elementi vengono trasformati in elementi di [riferimento](#reference) dalla `ResolveProjectReferences` destinazione, pertanto tutti i metadati validi per un riferimento potrebbero essere validi in `ProjectReference` , se il processo di trasformazione non lo sovrascrive.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Nome|Stringa facoltativa. Nome visualizzato del riferimento.|
|GlobalPropertiesToRemove|Oggetto `string[]` facoltativo. Nomi delle proprietà da rimuovere quando si compila il progetto a cui si fa riferimento, ad esempio `RuntimeIdentifier;PackOnBuild` . Per impostazione predefinita è vuoto.|
|Project|Stringa facoltativa. GUID per il riferimento, nel formato {12345678-1234-1234-1234-1234567891234}.|
|OutputItemType|Stringa facoltativa. Tipo di elemento in cui generare gli output di destinazione. Il valore predefinito è blank. Se i metadati di riferimento sono impostati su "true" (impostazione predefinita), gli output di destinazione diventeranno riferimenti per il compilatore.|
|ReferenceOutputAssembly|Valore booleano facoltativo. Se impostato su `false`, non include l'output del progetto a cui si fa riferimento come [riferimento](#reference) del progetto, ma assicura che l'altro progetto venga compilato prima di questo. Il valore predefinito è `true`.|
|SetConfiguration|Stringa facoltativa. Imposta la proprietà globale `Configuration` per il progetto a cui si fa riferimento, ad esempio `Configuration=Release` .|
|SetPlatform|Stringa facoltativa. Imposta la proprietà globale `Platform` per il progetto a cui si fa riferimento, ad esempio `Platform=AnyCPU` .|
|SetTargetFramework|Stringa facoltativa. Imposta la proprietà globale `TargetFramework` per il progetto a cui si fa riferimento, ad esempio `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|Valore booleano facoltativo. Se `true` , compila il progetto a cui si fa riferimento senza negoziare il valore più compatibile `TargetFramework` . Il valore predefinito è `false`.|
|Server di destinazione|Oggetto `string[]` facoltativo. Elenco di destinazioni separate da punto e virgola nei progetti a cui si fa riferimento da compilare. Per impostazione predefinita, il valore predefinito è `$(ProjectReferenceBuildTargets)` vuoto, che indica le destinazioni predefinite.|

## <a name="compile"></a>Compilazione

Rappresenta i file di origine per il compilatore.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| AutoGen | Valore booleano facoltativo. Indica se il file è stato generato per il progetto da Visual Studio Integrated Development Environment (IDE). |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del file di progetto. |
| Visible | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in Visual Studio. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori possibili sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

## <a name="embeddedresource"></a>EmbeddedResource

Rappresenta le risorse da incorporare nell'assembly generato.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato se il file si trova fisicamente fuori dall'influenza del progetto. |
| Visible | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in Visual Studio. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori possibili sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |
| LogicalName | Stringa obbligatoria. Nome logico della risorsa incorporata. |

## <a name="content"></a>Content

Rappresenta file che non sono compilati nel progetto, ma possono essere incorporati o pubblicati con il progetto.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file creato da qualsiasi generatore di file che è stato eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del progetto. |
| PublishState | Stringa obbligatoria. Lo stato di pubblicazione del contenuto, che può essere:<br /><br /> - Impostazione predefinita<br />- Incluso<br />- Escluso<br />- DataFile<br />- Prerequisito |
| IsAssembly | Valore booleano facoltativo. Specifica se il file è un assembly. |
| Visible | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in Visual Studio. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori possibili sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

## <a name="none"></a>nessuno

Rappresenta i file che non hanno un ruolo nel processo di compilazione.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del progetto. |
| Visible | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in Visual Studio. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori possibili sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

## <a name="assemblymetadata"></a>AssemblyMetadata

Rappresenta gli attributi di assembly da generare come `[AssemblyMetadata(key, value)]` .

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| Includi | Diventa il primo parametro (chiave) nel costruttore dell' `AssemblyMetadataAttribute` attributo. |
| Valore | Stringa obbligatoria. Diventa il secondo parametro (valore) nel costruttore dell' `AssemblyMetadataAttribute` attributo. |

> [!NOTE]
> Questo elemento si applica ai progetti che usano l'SDK per .NET 5 (e .NET Core) e versioni successive.

## <a name="internalsvisibleto"></a>InternalsVisibleTo

Specifica gli assembly da emettere come `[InternalsVisibleTo(..)]` attributi di assembly.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| Includi | Nome dell'assembly. |
| Chiave | Stringa facoltativa. Chiave pubblica dell'assembly. |

> [!NOTE]
> Questo elemento si applica ai progetti che usano l'SDK per .NET 5 (e .NET Core) e versioni successive.

## <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Rappresenta il manifesto dell'applicazione di base per la compilazione e contiene informazioni sulla sicurezza della distribuzione ClickOnce.

## <a name="codeanalysisimport"></a>CodeAnalysisImport

Rappresenta il progetto FxCop da importare.

## <a name="import"></a>Importa

Rappresenta gli assembly i cui spazi dei nomi devono essere importati dal compilatore Visual Basic.

## <a name="see-also"></a>Vedi anche

- [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)
- [Metadati dell'elemento MSBuild comuni](common-msbuild-item-metadata.md)
