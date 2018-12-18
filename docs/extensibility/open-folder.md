---
title: Panoramica di Visual Studio Apri cartella extensibility | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d916ea30dd9b72a2d8bd59e8d3d34f9e73c74877
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="open-folder-extensibility"></a>Estensibilità di cartella aperta

Il [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) funzionalità consente agli utenti di aprire una codebase in Visual Studio senza la necessità di file di progetto o soluzione. Apri cartella offre che agli utenti funzionalità aspettano da Visual Studio, ad esempio:

* Ricerca e integrazione di Esplora soluzioni
* Editor colorazione
* Vai a navigazione
* Trovare Cerca nei file

Se utilizzato con i carichi di lavoro ad esempio per lo sviluppo .NET e C++, ottengono anche gli utenti:

* Rich Intellisense
* Funzionalità specifiche della lingua

Con cartella aperta, gli autori delle estensioni possono creare funzionalità avanzate per qualsiasi lingua. Sono disponibili le API per il supporto di compilazione, debug e la ricerca dei simboli per qualsiasi file in un utente codebase. Extender corrente è possibile aggiornare le funzionalità di Visual Studio esistente per comprendere il codice senza il supporto di progetti o di una soluzione.

## <a name="an-api-without-project-systems"></a>Un'API senza sistemi di progetto

In passato, Visual Studio riconosciuti solo i file in una soluzione e i relativi progetti tramite sistemi di progetto. Un sistema di progetto è responsabile per le interazioni utente e funzionalità di un progetto caricato. Riconosce i file di progetto contiene la rappresentazione visiva del contenuto del progetto, le dipendenze in altri progetti e file di progetto di modifica dell'oggetto sottostante. È tramite queste gerarchie e le funzionalità di altri componenti utilizzabili per conto dell'utente. Non tutte le basi di codice sono anche rappresentati in una struttura di progetto e soluzione. Linguaggi di script e codice open source scritto in C++ per Linux sono i buoni esempi. Con cartella aperta, Visual Studio offre agli utenti un nuovo modo di interagire con il codice sorgente.

Le API di cartella aperta sono sotto il `Microsoft.VisualStudio.Workspace.*` dello spazio dei nomi e sono disponibili per estensioni produrre e usare i dati o azioni intorno file presenti nella cartella aperta. Le estensioni possono usare queste API per fornire funzionalità per le aree, tra cui:

- [Aree di lavoro](workspaces.md) : l'avvio di estendibilità di punto di cartella aperta è l'area di lavoro e le relative API.
- [File contesti e le azioni](workspace-file-contexts.md) -intelligence codice specifico fornito tramite contesti di file del File.
- [L'indicizzazione](workspace-indexing.md) : consente di raccogliere e rendere persistenti i dati sulle aree di lavoro di cartella aperta.
- [Servizi di linguaggio](workspace-language-services.md) -integrare servizi di linguaggio nelle aree di lavoro Apri cartella.
- [Compilare](workspace-build.md) -supporto per aree di lavoro di cartella aperta per la compilazione.

Funzionalità che utilizzano i tipi seguenti sarà necessario adottare nuove API per supportare Apri cartella:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commenti e suggerimenti, commenti, i problemi

Apri cartella e il `Microsoft.VisualStudio.Workspace.*` API sono in fase di sviluppo. Se viene visualizzato un comportamento imprevisto, quindi verificare i problemi noti per la versione di interesse. La Community degli sviluppatori è la posizione consigliata per votare e creare eventuali problemi. Per ogni commenti e suggerimenti, si consiglia una descrizione dettagliata del problema. Includere la versione di Visual Studio che per cui si sta sviluppando, le API in uso (viene implementata e si interagisce con), il risultato previsto e il risultato effettivo. Se possibile, includere un dump del processo devenv.exe. Utilizzo del problema di rilevamento per commenti e suggerimenti su questo e sulla relativa documentazione.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro](workspaces.md) -informazioni sull'area di lavoro Apri cartella API.