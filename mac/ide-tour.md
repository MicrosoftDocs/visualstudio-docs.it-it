---
title: Presentazione di Visual Studio per Mac | Microsoft Docs
description: Visual Studio per Mac offre un ambiente di sviluppo integrato per creare applicazioni .NET in macOS, inclusi siti Web ASP.NET Core e progetti Xamarin per iOS, Android, Mac e Xamarin.Forms.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: 0f8f3ba04d4e5a8949bc57cb8cf61d470690d786
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-for-mac-tour"></a>Presentazione di Visual Studio per Mac

Visual Studio per Mac fa evolvere Xamarin Studio, l'IDE di Xamarin incentrato sui dispositivi mobili, in un ambiente di sviluppo mobile-first, cloud-first per Mac. Questo strumento per sviluppatori permette di sfruttare la potenza di .NET per creare applicazioni per tutte le piattaforme, per soddisfare le esigenze degli utenti.

L'esperienza utente di Visual Studio per Mac è simile a quella della relativa controparte Windows, ma con un aspetto nativo tipico di macOS. La creazione, l'apertura e lo sviluppo di app saranno operazioni familiari per chi in precedenza ha usato Visual Studio in Windows. Visual Studio per Mac usa inoltre molti degli strumenti avanzati che rendono la controparte Windows un IDE estremamente potente. La piattaforma di compilazione Roslyn viene usata per il refactoring e per IntelliSense. Il sistema del progetto e il motore di compilazione usano MSBuild e l'editor standard supporta i bundle TextMate. Vengono usati gli stessi motori di debugger per le app Xamarin e .NET Core e le stesse finestre di progettazione per Xamarin.iOS e Xamarin.Android.

Questo articolo esamina diverse sezioni di Visual Studio per Mac e presenta alcune delle caratteristiche che lo rendono uno strumento potente per la creazione di applicazioni multipiattaforma.

## <a name="ide-tour"></a>Presentazione dell'IDE

Visual Studio per Mac è organizzato in sezioni diverse per la gestione di impostazioni e file delle applicazioni, la creazione di codice delle applicazioni e il debug.

## <a name="welcome-screen"></a>Schermata iniziale

All'avvio, Visual Studio per Mac visualizza una *schermata iniziale*, come illustrato di seguito:

![Schermata iniziale](media/ide-tour-image1.png)

La schermata iniziale contiene le sezioni seguenti:

- **Barra degli strumenti** - Consente l'accesso rapido alla barra di ricerca. Quando viene caricata una soluzione, questa barra viene usata per definire le configurazioni dell'app, per eseguire il debug e per visualizzare gli errori.
- **Guida introduttiva** - Consente l'accesso rapido ad argomenti utili per gli sviluppatori, per iniziare a usare Visual Studio per Mac.
- **Soluzioni recenti** - Consente l'accesso rapido alle soluzioni aperte di recente, oltre che fornire comodi pulsanti per aprire o creare progetti.
- **Novità per gli sviluppatori** - Un newsfeed che offre aggiornamenti sulle ultime novità per gli sviluppatori Microsoft.

## <a name="solutions-and-projects"></a>Soluzioni e progetti

L'immagine seguente mostra Visual Studio per Mac con un'applicazione caricata:

![Visual Studio per Mac con un'applicazione caricata](media/ide-tour-image17.png)

Le sezioni seguenti forniscono una panoramica delle principali aree di Visual Studio per Mac.

## <a name="solution-pad"></a>Riquadro della soluzione

Il riquadro della soluzione organizza i progetti in una soluzione, come illustrato di seguito:

![Progetti organizzati nel riquadro della soluzione](media/ide-tour-image18.png)

In questa posizione i file per il codice sorgente, le risorse, l'interfaccia utente e le dipendenze vengono organizzati in progetti specifici della piattaforma.

Per altre informazioni sull'uso di progetti e soluzioni in Visual Studio per Mac, vedere [Progetti e soluzioni](~/projects-and-solutions.md).

## <a name="assembly-references"></a>Riferimenti dell'assembly
 
I riferimenti ad assembly per ogni progetto sono disponibili nella cartella Riferimenti illustrata di seguito:

![Cartella Riferimenti nel riquadro della soluzione](media/ide-tour-image19.png)

È possibile aggiungere altri riferimenti usando la finestra di dialogo **Modifica riferimenti**, visualizzata facendo doppio clic sulla cartella Riferimenti oppure scegliendo **Modifica riferimenti** tra le azioni del menu di scelta rapida:
 
![Finestra di dialogo Modifica riferimenti](media/ide-tour-image20.png)

Per altre informazioni sull'uso dei riferimenti in Visual Studio per Mac, vedere l'argomento [Gestione dei riferimenti in un progetto](~/managing-references-in-a-project.md).

## <a name="dependencies--packages"></a>Dipendenze/pacchetti

Tutte le dipendenze esterne usate nell'app vengono archiviate nella cartella Dipendenze o Pacchetti, a seconda che si stia lavorando a un progetto .NET Core o Xamarin.iOS/Xamarin.Android. In genere vengono fornite sotto forma di componente o pacchetto NuGet.

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Con il supporto di NuGet di Visual Studio è possibile cercare e aggiungere facilmente pacchetti al progetto dell'applicazione.

Per aggiungere una dipendenza all'applicazione, fare clic con il pulsante destro del mouse sulla cartella Dipendenze/Pacchetti e scegliere **Aggiungi pacchetti**:

![Aggiungere un pacchetto NuGet](media/ide-tour-image21.png)

Le informazioni sull'uso di un pacchetto NuGet in un'applicazione sono disponibili nell'argomento [Inserimento di un pacchetto NuGet nel progetto](~/nuget-walkthrough.md).

## <a name="refactoring"></a>Refactoring

Visual Studio per Mac fornisce due metodi utili per il refactoring del codice: azioni di contesto e analisi dell'origine. Per altre informazioni, vedere l'argomento [Refactoring](~/refactoring.md).

## <a name="debugging"></a>Debug

Visual Studio per Mac ha un debugger nativo che offre supporto per il debug per applicazioni Xamarin.iOS, Xamarin.Mac e Xamarin.Android. Visual Studio per Mac usa Mono Soft Debugger, un debugger implementato nel runtime di Mono, per consentire all'IDE di eseguire il debug di codice gestito in tutte le piattaforme. Per altre informazioni sul debug, vedere l'argomento [Debug](~/debugging.md).

Il debugger contiene visualizzatori avanzati per tipi speciali come stringhe, colori, URL, oltre che dimensioni, coordinate e curve di Bézier.

Per altre informazioni sulle visualizzazioni dei dati del debugger, vedere l'argomento [Visualizzazioni dei dati](~/data-visualizations.md).

## <a name="version-control"></a>Controllo della versione

Visual Studio per Mac si integra con sistemi di controllo del codice sorgente Subversion e Git. I progetti sottoposti a controllo del codice sorgente sono contrassegnati con un ramo accanto al nome della soluzione: 

![Nome del ramo per indicare un progetto sottoposto a controllo del codice sorgente](media/ide-tour-image22.png)

I file con modifiche non sottoposte a commit presentano un'annotazione sulle icone nel riquadro della soluzione, come illustrato di seguito:

![File con modifiche non sottoposte a commit nel riquadro della soluzione](media/ide-tour-image23.png)

Per altre informazioni sul controllo della versione in Visual Studio, vedere l'argomento [Controllo della versione](~/version-control.md).