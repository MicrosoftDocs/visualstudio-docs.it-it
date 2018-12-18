---
title: Suggerimenti sulle prestazioni di Visual Studio | Microsoft Docs
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3a48166490cb48870e9e6341b0cba6dfc9f668fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Suggerimenti sulle prestazioni di Visual Studio

I suggerimenti per le prestazioni di Visual Studio si riferiscono a situazioni di memoria insufficiente che possono verificarsi in casi eccezionali. In queste situazioni, è possibile ottimizzare determinate funzionalità di Visual Studio che potrebbero non essere in uso. I suggerimenti seguenti non sono intesi come indicazioni generali.

> [!NOTE]
> In caso di difficoltà di uso del prodotto a causa di problemi di memoria, segnalarlo tramite lo strumento di feedback.

## <a name="optimize-your-environment"></a>Ottimizzazione dell'ambiente

- **Usare un sistema operativo a 64 bit**

    Se si aggiorna il sistema da una versione di Windows a 32 bit a una versione a 64 bit, espandere la quantità di memoria virtuale disponibile per Visual Studio da 2 a 4 GB. Ciò consente a Visual Studio di gestire carichi di lavoro notevolmente più grandi anche tramite il processo a 32 bit.

    Per altre informazioni, vedere [Limiti di memoria](https://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) e [Uso di /LARGEADDRESSAWARE in Windows a 64 bit](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Configurare soluzione e progetti

In caso di una soluzione molto grande con molti progetti, possono essere utili le ottimizzazioni seguenti:

- **Scaricare progetti**

    È possibile scaricare manualmente singoli progetti utilizzati raramente da Esplora soluzioni usando il menu di scelta rapida.

- **Eseguire il refactoring della soluzione**

    È possibile suddividere la soluzione in diversi file di soluzione più piccoli con i progetti usati comunemente. Questo refactoring dovrebbe ridurre notevolmente utilizzo della memoria per il flusso di lavoro. Inoltre le soluzioni di dimensioni inferiori si caricano più velocemente.

## <a name="configure-debugging-options"></a>Configurare le opzioni di debug

Se in genere si verificano problemi di memoria insufficiente durante le sessioni di debug, è possibile ottimizzare le prestazioni apportando una o più modifiche alla configurazione.

- **Abilitare Just My Code**

    L'ottimizzazione più semplice consiste nell'abilitazione della funzionalità **Just My Code** che carica solo i simboli per il proprio progetto. L'abilitazione di questa funzionalità può offrire un notevole risparmio di memoria per il debug delle applicazioni gestite (.NET). Questa opzione è già abilitata per impostazione predefinita in alcuni tipi di progetto.

    Per abilitare **Just My Code**, scegliere **Strumenti > Opzioni > Debug > Generale**, quindi selezionare **Abilita Just My Code**.

- **Specificare i simboli da caricare**

    Per il debug nativo, il caricamento dei file di simboli (con estensione PDB) è dispendioso in termini di risorse di memoria. È possibile configurare le impostazioni dei simboli del debugger per risparmiare memoria. In genere, si configura la soluzione per caricare solo i moduli del proprio progetto.

    Per specificare il caricamento dei simboli, scegliere **Strumenti > Opzioni > Debug > Simboli**.

    Impostare le opzioni su **Solo moduli specificati** anziché su **Tutti i moduli** e quindi specificare quali moduli si intende caricare. Durante il debug, è anche possibile fare doppio clic su moduli specifici nella finestra **Moduli** per includere in modo esplicito un modulo nel caricamento dei simboli (per aprire la finestra durante il debug, scegliere **Debug > Finestra > Moduli**).

    Per altre informazioni, vedere [Informazioni sui file dei simboli](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Disabilitare gli strumenti di diagnostica**

    È consigliabile disabilitare la profilatura della CPU dopo l'uso. Questa funzionalità può utilizzare grandi quantità di risorse. Dopo aver abilitato la profilatura della CPU, questo stato viene mantenuto per le sessioni di debug successive, perciò è preferibile disattivarla al termine. È possibile risparmiare risorse disabilitando gli strumenti di diagnostica durante il debug se la funzionalità offerte non sono necessarie.

    Per disabilitare gli strumenti di diagnostica, avviare una sessione di debug, scegliere **Strumenti > Opzioni > Abilita strumenti di diagnostica** e deselezionare l'opzione.

    Per altre informazioni, vedere [Strumenti di profilatura](../profiling/profiling-tools.md).

## <a name="disable-tools-and-extensions"></a>Disabilitare strumenti ed estensioni

Alcuni strumenti o estensioni possono essere disattivati per migliorare le prestazioni.

> [!TIP]
> È in genere possibile isolare i problemi di prestazioni disattivando le estensioni una alla volta e ricontrollando le prestazioni.

### <a name="managed-language-services-roslyn"></a>Servizi di linguaggio gestiti (Roslyn)

Per informazioni sulle prestazioni di .NET Compiler Platform ("Roslyn"), vedere [Considerazioni sulle prestazioni di soluzioni di grandi dimensioni] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Disabilitare l'analisi della soluzione completa**

    Visual Studio esegue l'analisi dell'intera soluzione per fornire un'esperienza completa di verifica degli errori prima di richiamare una compilazione. Questa funzionalità è utile per identificare gli errori il più presto possibile. Tuttavia, in caso di soluzioni molto grandi, può richiedere risorse di memoria notevoli. In caso di memoria insufficiente o di problemi analoghi, è possibile disabilitare questa funzionalità per liberare risorse. Per impostazione predefinita, questa opzione è abilitata per Visual Basic ed è disabilitata per C#.

    Per disabilitare l'**analisi della soluzione completa**, scegliere **Strumenti > Opzioni > Editor di testo > <Visual Basic o C#>**. Quindi scegliere **Avanzate** e deselezionare **Abilita analisi della soluzione completa**.

- **Disabilitare CodeLens**

    Visual Studio esegue un'attività **Trova tutti i riferimenti** su ogni metodo quando viene visualizzato. CodeLens offre funzionalità come la visualizzazione inline del numero di riferimenti. Il lavoro viene eseguito in un processo separato (ad esempio, ServiceHub.RoslynCodeAnalysisService32). In soluzioni molto grandi o in sistemi con risorse limitate, questa funzionalità può avere un impatto notevole sulle prestazioni anche se viene eseguita con bassa priorità. Se si riscontra un elevato utilizzo della CPU in questo processo o se si verificano problemi di memoria (ad esempio, durante il caricamento di una soluzione di grandi dimensioni in un computer da 4 GB), è possibile provare a disabilitare questa funzionalità per liberare risorse.

    Per disabilitare CodeLens, scegliere **Strumenti > Opzioni > Editor di testo > Tutti i linguaggi > CodeLens** e deselezionare la funzionalità.

    Questa funzionalità è disponibile in Visual Studio Professional e in Visual Studio Enterprise.

### <a name="other-tools-and-extensions"></a>Altri strumenti ed estensioni

- **Disabilitare le estensioni**

    Le estensioni sono componenti software aggiuntivi aggiunti di Visual Studio che offrono nuove funzionalità o estendono le funzionalità esistenti. Le estensioni possono spesso dare origine a problemi di memoria. Se si verificano problemi di memoria, provare a disabilitare estensioni una alla volta per verificarne l'impatto su scenario o flusso di lavoro.

    Per disabilitare le estensioni, andare a **Strumenti | Estensioni e aggiornamenti** e disabilitare l'estensione specifica.

- **Disabilitare la finestra di progettazione XAML**

    La finestra di progettazione XAML è abilitata per impostazione predefinita ma utilizza risorse solo se si apre un file con XAML. Se si utilizzano file XAML ma non si intende usare la funzionalità della finestra di progettazione, disabilitare questa funzionalità per liberare memoria.

    Per disabilitare la finestra di progettazione XAML, andare a **Strumenti > Opzioni > Finestra di progettazione XAML > Abilita finestra di progettazione XAML** e deselezionare l'opzione.

- **Rimuovere i carichi di lavoro**

    È possibile utilizzare il programma di installazione di Visual Studio per rimuovere i carichi di lavoro che non vengono più utilizzati. Questa azione può ridurre le esigenze di memoria di avvio ed esecuzione escludendo i pacchetti e gli assembly non più necessari.

## <a name="force-a-garbage-collection"></a>Imporre una Garbage Collection

CLR usa una sistema di gestione della memoria di Garbage Collection. In questo sistema, talvolta viene utilizzata memoria da oggetti non più necessari. Questo stato è temporaneo, il Garbage Collector libera questa memoria in base alla propria euristica di prestazioni e uso delle risorse. È possibile imporre a CLR la raccolta della memoria inutilizzata usando un tasto di scelta rapida in Visual Studio. Se è presente una quantità notevole di garbage in attesa di raccolta e si impone una Garbage Collection, si dovrebbe notare una riduzione nel consumo di memoria da parte del processo devenv.exe in Gestione attività. È raramente è necessario utilizzare questo metodo. Tuttavia, dopo il completamento di un'operazione dispendiosa (ad esempio una compilazione completa, una sessione di debug o un evento di apertura della soluzione), può consentire di determinare la quantità di memoria effettivamente usata dal processo. Poiché Visual Studio è misto (gestito e nativo), è talvolta possibile che allocatore nativo e Garbage Collector si contengono le risorse di memoria. In condizioni di utilizzo elevato della memoria, può essere utile per imporre l'esecuzione del Garbage Collector.

Per imporre una Garbage Collection, usare il tasto di scelta rapida: **Ctrl+Alt+Maiusc+F12**, **Ctrl+Alt+Maiusc+F12** (premerlo due volte).

Se l'imposizione della Garbage Collection risulta particolarmente efficiente nel proprio scenario, compilare un report tramite lo strumento per il feedback di Visual Studio poiché questo comportamento è in genere sintomo di un bug.

Per una descrizione dettagliata del Garbage Collector di CLR, vedere [Nozioni fondamentali sulla Garbage Collection](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Vedere anche

[IDE di Visual Studio](../ide/visual-studio-ide.md)
