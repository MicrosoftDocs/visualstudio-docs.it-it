---
title: 'Procedura: round trip estensioni per Visual Studio | Documenti Microsoft'
ms.custom: ''
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 9d8d0dc2e5c8c95b5f2502ef5a48e6f97c26e289
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Procedura: creare estensioni compatibile con Visual Studio 2017 e Visual Studio 2015

Questo documento viene illustrato come creare progetti di estendibilità round trip tra Visual Studio 2015 e Visual Studio 2017. Dopo aver completato l'aggiornamento, un progetto sarà in grado di aprire, compilare, installare ed eseguire sia in Visual Studio 2015 che Visual Studio 2017.  Come riferimento, è possano trovare alcune estensioni che possono essere round trip tra Visual Studio 2015 e Visual Studio 2017 [qui](https://github.com/Microsoft/VSSDK-Extensibility-Samples) negli esempi di estendibilità di Microsoft.

Se si intende solo creato in Visual Studio 2017, ma desidera output VSIX per l'esecuzione sia in Visual Studio 2015 che Visual Studio 2017, quindi fare riferimento al [estensione migrazione documento](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Nota:** a causa di modifiche in Visual Studio tra le versioni, le operazioni che funziona correttamente in una versione non funzionerà un altro. Verificare che le funzionalità che si sta tentando di accedere a sono disponibili in entrambe le versioni o avrà l'estensione risultati imprevisti.

Di seguito è riportato un riepilogo della procedura che si completeranno in questo documento per il round trip a un progetto VSIX:

1. Importazione di pacchetti NuGet corretti.
2. Aggiornare il manifesto di estensione:
    * Destinazione di installazione
    * Prerequisiti
3. Aggiornare CSProj:
    * Aggiornamento `<MinimumVisualStudioVersion>`.
    * Aggiungere il `<VsixType>` proprietà.
    * Aggiungere la proprietà di debug `($DevEnvDir)` 3 volte.
    * Aggiungere le condizioni per l'importazione di strumenti di compilazione e destinazioni.

4. Compilazione e Test

## <a name="environment-setup"></a>Impostazione dell'ambiente

Questo documento si presuppone di aver installato nel computer di quanto segue:

* Visual Studio 2015 con installato il SDK di Visual Studio
* Visual Studio 2017, con il carico di lavoro di estendibilità installato

## <a name="recommended-approach"></a>Approccio consigliato

Si consiglia di iniziare l'aggiornamento con Visual Studio 2015, invece di Visual Studio 2017. Il vantaggio principale dell'ambiente di sviluppo Visual Studio 2015 è garantire che non fanno riferimento gli assembly che non sono disponibili in Visual Studio 2015. Se si esegue l'operazione di sviluppo in Visual Studio 2017, sussiste il rischio che si potrebbe introdurre una dipendenza su un assembly che esiste solo in Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Verificare che sia presente alcun riferimento al file Project. JSON

Più avanti in questo documento, si inserirà istruzioni di importazione condizionale al file *. csproj.  Questo non funzionerà se vengono archiviati i riferimenti di NuGet in Project. JSON. Di conseguenza, è consigliabile spostare tutti i riferimenti di NuGet nel file Packages.
Se il progetto contiene un file Project JSON:

* Prendere nota dei riferimenti in Project. JSON.
* In Esplora soluzioni, eliminare il file di Project dal progetto.
    * Questo elimina il file Project JSON, ma verrà rimosso dal progetto.
* Aggiungere che i riferimenti di NuGet nuovamente al progetto.
    * Pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet per la soluzione...**
    * Visual Studio crea automaticamente il file Packages config di

>**Nota:** se il progetto contiene pacchetti EnvDTE, devono essere aggiunti con il pulsante destro facendo clic su **riferimenti** selezionando **aggiungere riferimento** e l'aggiunta del riferimento appropriato.  Utilizzo di pacchetti NuGet può creare errori durante il tentativo di compilare il progetto.

## <a name="adding-appropriate-build-tools"></a>Aggiunta di strumenti di compilazione appropriati

È necessario assicurarsi di aggiungere strumenti di compilazione che consentono di compilare ed eseguire il debug in modo appropriato. Microsoft ha creato un assembly per questa chiamata Microsoft.VisualStudio.Sdk.BuildTasks.

Per compilare e distribuire un VSIXv3 in Visual Studio 2015 sia 2017, sono necessari i pacchetti NuGet seguenti:

Versione | Strumenti incorporati
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

A tale scopo:

* Aggiungere il pacchetto NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 al progetto.
* Se il progetto non contiene Microsoft.VSSDK.BuildTools, aggiungerlo.
* Verificare la versione Microsoft.VSSDK.BuildTools sia 15.x o versione successiva.

## <a name="update-extension-manifest"></a>Aggiornare il manifesto di estensione

### <a name="1-installation-targets"></a>1. Destinazioni di installazione

È necessario indicare a Visual Studio quali versioni di destinazione per la compilazione di un progetto VSIX.  In genere, questi riferimenti sono in versione 14.0 (Visual Studio 2015) o versione 15.0 (Visual Studio 2017).  In questo caso, si desidera compilare un progetto VSIX che consentirà di installare un'estensione per entrambi, pertanto è necessario che entrambe le versioni di destinazione.  Se si desidera il progetto VSIX per creare e installare nelle versioni precedenti a 14.0, si possono eseguire impostando il numero di versione precedente. Tuttavia, 10.0 e versioni precedenti non sono più supportate.

* Aprire il file vsixmanifest in Visual Studio.
* Aprire il **destinazioni di installazione** scheda.
* Modifica il **intervallo versione** per [14,0, 16,0).  Il ' [' indica per includere 14,0 e tutte le versioni precedenti, Visual Studio.  Il ')' indica a Visual Studio per includere tutte le versioni di 15.0 backup, ma non include versione 16,0.
* Salvare tutte le modifiche e chiudere tutte le istanze di Visual Studio.

![Immagine di destinazioni di installazione](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Aggiunta di prerequisiti per il file extension vsixmanifest

Prerequisiti sono una nuova funzionalità con Visual Studio 2017.  In questo caso, è necessario l'Editor di componenti di base di Visual Studio come prerequisito. Poiché la finestra di progettazione di Visual Studio 2015 VSIX non consente di gestire il nuovo `Prerequisites` sezione, è necessario modificare questa parte manualmente nel codice XML.  In alternativa, è possibile aprire Visual Studio 2017 e utilizzare la finestra di progettazione manifesto aggiornato per inserire i prerequisiti.

Effettuare questa operazione manualmente:

* Passare alla directory del progetto in Esplora File.
* Aprire il `extension.vsixmanifest` file con un editor di testo.
* Aggiungere il seguente tag:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Salvare e chiudere il file.

>**Nota:** se si sceglie di farlo con Progettazione modelli di progetto VSIX in Visual Studio 2017, sarà necessario modificare manualmente la versione dei prerequisiti per assicurarsi che sia compatibile con tutte le versioni di Visual Studio 2017.  Questo avviene perché la finestra di progettazione verrà inserita la versione minima come la versione corrente di Visual Studio (ad esempio, 15.0.26208.0).  Tuttavia, poiché altri utenti possono avere una versione precedente, è possibile modificare manualmente questa opzione per 15.0.

A questo punto, il file manifesto dovrebbe essere simile al seguente:

![Esempio di prerequisiti](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificare il file di progetto (MyProject. csproj)

Si consiglia un riferimento a un file con estensione csproj modificato aperto durante l'esecuzione di questo passaggio.  È possibile trovare alcuni esempi [qui](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Selezionare qualsiasi esempio di estendibilità, trovare il file con estensione csproj come riferimento ed eseguire i passaggi seguenti:

* Passare alla directory del progetto in Esplora File.
* Aprire il file MyProject. csproj con un editor di testo.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aggiornare il MinimumVisualStudioVersion

* Impostare la versione di visual studio minimo `$(VisualStudioVersion)` e aggiungere un'istruzione condizionale per tale.  Se non sono presenti, aggiungere questi tag.  Verificare che i tag siano impostati come indicato di seguito:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Aggiungere la proprietà VsixType

* Aggiungere il seguente tag `<VsixType>v3</VsixType>` a un gruppo di proprietà.

>**Nota:** si consiglia di aggiungere questo elemento sotto il `<OutputType></OutputType>` tag.

### <a name="3-add-the-debugging-properties"></a>3. Aggiungere le proprietà di debug

* Aggiungere il gruppo di proprietà seguenti:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminare tutte le istanze degli elementi seguenti dal file con estensione csproj e qualsiasi. csproj file:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Aggiungere condizioni per le importazioni di strumenti di compilazione

* Aggiungere ulteriori istruzioni condizionali di `<import>` tag che dispone di un riferimento Microsoft.VSSDK.BuildTools.  A tale scopo l'inserimento di `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione condizionale.  Queste istruzioni verranno visualizzato nell'intestazione e piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Aggiungere ulteriori istruzioni condizionali di `<import>` tag che hanno un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  A tale scopo l'inserimento di `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione condizionale. Queste istruzioni verranno visualizzato nell'intestazione e piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Aggiungere ulteriori istruzioni condizionali di `<Error>` tag che dispone di un riferimento Microsoft.VSSDK.BuildTools.  A tale scopo l'inserimento di `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione condizionale. Queste istruzioni verranno visualizzata nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Aggiungere ulteriori istruzioni condizionali di `<Error>` tag che hanno un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  A tale scopo l'inserimento di `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione condizionale. Queste istruzioni verranno visualizzata nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Salvare il file csproj e chiuderlo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Installa l'estensione di test in Visual Studio 2015 e Visual Studio 2017

A questo punto, il progetto deve essere pronto per la compilazione di un VSIXv3 che è possibile installare Visual Studio 2015 e Visual Studio 2017.

* Aprire il progetto in Visual Studio 2015
* Compilare il progetto e verificare nell'output di un progetto VSIX venga compilata correttamente
* Passare alla directory del progetto
* Aprire il cassetto -> Debug cartella
* Fare doppio clic sul file VSIX e installare l'estensione in Visual Studio 2015 e Visual Studio 2017
* Verificare che è possibile visualizzare l'estensione in Strumenti -> estensioni e aggiornamenti nella sezione "Installazione".
* Tentativo di esecuzione/Usa l'estensione per verificare che il funzionamento

![Ricerca di un progetto VSIX](media/finding-a-VSIX-example.png)

>**Nota:** se il progetto si blocca con il messaggio "Impossibile aprire il file" force chiuso Visual Studio, passare alla directory del progetto, visualizzare le cartelle nascoste ed eliminare la cartella VS.
