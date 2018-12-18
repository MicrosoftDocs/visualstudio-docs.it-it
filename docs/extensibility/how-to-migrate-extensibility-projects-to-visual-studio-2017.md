---
title: "Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017 | Documenti Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d49ff89f38b0279c60f49ee7d5856d21fd5fc4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017

Questo documento illustra come aggiornare i progetti di estendibilità di Visual Studio 2017. Oltre a descrivere la procedura per aggiornare i file di progetto, viene inoltre descritto come eseguire l'aggiornamento dalla versione del manifesto dell'estensione 2 (v2 VSIX) per il nuova versione 3 formato del manifesto VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installare Visual Studio 2017 con carichi di lavoro richiesti

Verificare che l'installazione include i carichi di lavoro seguenti:

* Sviluppo per desktop .NET
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire una soluzione VSIX in Visual Studio 2017

Tutti i progetti VSIX richiederanno un aggiornamento unidirezionale di versione principale di Visual Studio 2017.

Verrà aggiornato il file di progetto (ad esempio *. csproj):

* MinimumVisualStudioVersion - è ora impostato su 15.0
* OldToolsVersion (se esiste già)-ora impostato su 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto Microsoft.VSSDK.BuildTools NuGet

>**Nota:** se la soluzione non fa riferimento il pacchetto Microsoft.VSSDK.BuildTools NuGet, è possibile ignorare questo passaggio.

Per compilare l'estensione di v3 VSIX nuovo formato (versione 3), è necessario compilare con i nuovi strumenti di compilazione di VSSDK la soluzione. Verrà installata con Visual Studio 2017, ma l'estensione v2 VSIX potrebbe contenere un riferimento a una versione precedente tramite NuGet. In questo caso, è necessario installare manualmente un aggiornamento del pacchetto Microsoft.VSSDK.BuildTools NuGet per la soluzione.

Per aggiornare i riferimenti di NuGet per Microsoft.VSSDK.BuildTools:

* Pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet per la soluzione...**
* Passare il **aggiornamenti** scheda.
* Selezionare Microsoft.VSSDK.BuildTools (versione più recente).
* Premere **aggiornamento**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportare modifiche al manifesto dell'estensione VSIX

Per verificare che tutti gli assembly necessari per eseguire l'estensione per l'installazione dell'utente di Visual Studio, specificare tutti i componenti dei prerequisiti o i pacchetti nel file manifesto dell'estensione. Quando un utente tenta di installare l'estensione, il VSIXInstaller controllerà se tutti i prerequisiti siano installati. Se mancano alcuni, l'utente verrà richiesto di installare i componenti mancanti come parte del processo di installazione di estensione.

>**Nota:** , tutte le estensioni devono specificare almeno il componente editor principale di Visual Studio come prerequisito.

* Modificare il file manifesto dell'estensione (in genere chiamato vsixmanifest).
* Verificare `InstallationTarget` include 15.0.
* Aggiungere i prerequisiti di installazione richiesti (come illustrato nell'esempio riportato di seguito).
  * È consigliabile che specificare solo ID di componenti dei prerequisiti.
  * Vedere la sezione alla fine di questo documento per [istruzioni sull'identificazione degli ID componente](#finding-component-ids).

Esempio:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opzione: Utilizzare la finestra di progettazione per apportare modifiche al manifesto dell'estensione VSIX

Invece di modificare direttamente il codice XML del manifesto, è possibile utilizzare il nuovo **prerequisiti** scheda nella finestra di progettazione manifesto per selezionare i prerequisiti e il codice XML verrà aggiornata automaticamente.

>**Nota:** progettazione manifesto solo consente di selezionare i componenti (non pacchetti o i carichi di lavoro) installati nell'istanza corrente di Visual Studio. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente che non è attualmente installato, è possibile modificare direttamente il manifesto XML.

* Aprire il file vsixmanifest [Progettazione].
* Selezionare **prerequisiti** scheda e premere **New** pulsante.

  ![Finestra di progettazione manifesto VSIX](media/vsix-manifest-designer.png)

* Il **aggiungere nuovi prerequisiti** aprirà la finestra.

  ![aggiungere il prerequisito vsix](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a discesa per **nome** e selezionare il prerequisito desiderato.
* Se necessario, aggiornare la versione.

  >Nota: Il campo versione sarà già popolato con la versione del componente attualmente installato, con un intervallo che si estende su fino a (ma non inclusi) la successiva versione principale del componente.

  ![aggiungere il prerequisito roslyn](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>Aggiornare le impostazioni di Debug per il progetto

Se si desidera eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che le impostazioni di progetto per **Debug** > **azione di avvio** ha il **avviare esterno programma:** valore impostato per il file devenv.exe dell'installazione di Visual Studio 2017.

Potrebbe essere simile:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Avvia programma esterno](media/start-external-program.png)

>**Nota:** l'azione di avvio Debug è in genere archiviato nel. file csproj. Questo file è in genere inclusa nel file con estensione gitignore e, di conseguenza, non viene in genere salvato con altri file di progetto quando vengono salvate nel controllo del codice sorgente. Di conseguenza, se si have estratti la soluzione aggiornata dal controllo del codice sorgente è probabile che il progetto non avrà nessun valore impostato per l'azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 avrà un. file csproj creato con le impostazioni predefinite che punta alla directory di installazione corrente di Visual Studio. Tuttavia se si esegue la migrazione di un'estensione v2 VSIX, è probabile che il. csproj file conterrà i riferimenti a directory di installazione della versione di Visual Studio precedente. Impostazione del valore per **Debug** > **azione di avvio** consentirà l'istanza sperimentale di Visual Studio corretto da avviare quando si tenta di eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione venga compilata correttamente (come un v3 VSIX)

* Compilare il progetto VSIX.
* Decomprimere il progetto VSIX generato.
  * Per impostazione predefinita, l'utilizzo di file VSIX in bin/Debug o bin/versione come estensione VSIX [YourCustomExtension].
  * Rinominare ZIP visualizzare facilmente il contenuto VSIX.
* Verificare l'esistenza di tre file:
  * Extension. vsixmanifest
  * manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Controllare se sono installati tutti i prerequisiti necessari

Verificare che il progetto VSIX viene installato correttamente in un computer con tutte le necessarie siano installati i prerequisiti.

>**Nota:** prima di installare qualsiasi estensione, chiudere tutte le istanze di Visual Studio.

Tentativo di installare l'estensione:

* In Visual Studio 2017

![Programma di installazione VSIX in Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltativo: Controllare le versioni precedenti di Visual Studio.
  * Prova di compatibilità con le versioni precedenti.
  * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltativo: Verificare che il controllo di versione di VSIX Installer offre una gamma di versioni.
  * Include le versioni precedenti di Visual Studio (se installato).
  * Include 2017 di Visual Studio.

Se Visual Studio è stato aperto di recente, verranno visualizzati una finestra di dialogo simile alla seguente:

![Visual Studio, i processi in esecuzione](media/vs-running-processes.png)

Attendere che il processo da arrestare o terminare manualmente le attività. È possibile trovare i processi da quello elencato o con il PID elencati tra parentesi.

>**Nota:** questi processi non verranno automaticamente chiuso durante l'esecuzione di un'istanza di Visual Studio. Assicurarsi di aver arrestare tutte le istanze di Visual Studio nel computer, comprese quelle di altri utenti, quindi continuare a ripetere.

## <a name="check-when-missing-the-required-prerequisites"></a>Controllare se mancano i prerequisiti necessari

* Tentativo di installare l'estensione in un computer con Visual Studio 2017 che non contengono tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifica il componente mancante/s e li elenca come prerequisito nel VSIXInstaller.
* Nota: L'elevazione dei privilegi sarà obbligatoria se tutti i prerequisiti devono essere installati con l'estensione.

![Prerequisito mancante vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Scelta di componenti

Quando si cercano le dipendenze, si noterà che una dipendenza può eseguire il mapping a più componenti. Per determinare le dipendenze di cui è necessario specificare il prerequisito, è consigliabile scegliere un componente che dispone di una funzionalità simile per l'estensione e di considerare anche gli utenti e il tipo di componenti sarebbe probabilmente installati o non è presente l'installazione. È anche consigliabile compilazione estensioni in un modo in cui i prerequisiti necessari soddisfano solo il valore minimo che consente l'estensione per l'esecuzione e per altre funzionalità siano inattivi se alcuni componenti non vengono rilevati.

Per fornire ulteriori istruzioni, sono state identificate alcuni tipi di estensione comuni e sui relativi prerequisiti suggeriti:

Tipo di estensione | Nome visualizzato | Id
--- | --- | ---
Editor | Editor principale di Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base Carico di lavoro desktop gestito | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger JIT | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>ID di componenti di ricerca

L'elenco dei componenti ordinati in base al prodotto di Visual Studio è in [il carico di lavoro di Visual Studio 2017 e gli ID componente](https://aka.ms/vs2017componentIDs). Utilizzare questi ID componente per gli ID dei prerequisiti nel manifesto.

Se non si conosce il componente che contiene un download di file binari, specifici di [componenti -> foglio di calcolo di mapping dei tipi binari](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Esistono quattro colonne nel foglio di Excel: **nome componente**, **ComponentId**, **versione**, e **binario o nomi di File**.  È possibile utilizzare i filtri per cercare e trovare i file binari e componenti specifici.

Per tutti i riferimenti prima di tutto determinare quelle nel componente principale editor (Microsoft.VisualStudio.Component.CoreEditor).  Come minimo, è necessario il componente editor di componenti di base per essere specificato come prerequisito per tutte le estensioni. Di riferimenti rimanenti che non sono presenti nell'editor di componenti di base, aggiungere filtri nel **file binari o nomi di file** sezione per i componenti che includono qualsiasi subset di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e che il progetto ha un riferimento a VSDebugEng.dll e VSDebug.dll, fare clic sul pulsante del filtro nel **file binari o nomi di file** intestazione.  Cercare "VSDebugEng.dll" e selezionare OK.  Successivamente fare clic sul pulsante del filtro nel **file binari o nomi di file** intestazione nuovamente e cercare "VSDebug.dll".  Selezionare la casella di controllo "Aggiungi selezione corrente al filtro" e selezionare OK.  Ora esaminare il **nome componente** per trovare un componente che è la maggior parte delle relative al tipo di estensione. In questo esempio scelto Just-In-Time del debugger e verrà aggiunto il vsixmanifest.
* Se si sa che il progetto si occupa elementi debugger, è possibile cercare "debugger" nella casella di ricerca di filtro per visualizzare i componenti contengono debugger nel nome.

## <a name="specifying-a-visual-studio-2017-release"></a>Specificare una versione di Visual Studio 2017

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, una funzionalità rilasciata in 15.3 dipende, è necessario specificare il numero di build in un progetto VSIX del **la destinazione di installazione**. Ad esempio, versione 15.3 presenta un numero di build di '15.0.26730.3'. È possibile visualizzare il mapping delle versioni per i numeri di build [qui](../install/visual-studio-build-numbers-and-release-dates.md). Utilizzando il numero di versione '15.3' non funzionerà correttamente.

Se l'estensione richiede 15.3 o versioni successive, è necessario dichiarare il **la destinazione di installazione versione** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```