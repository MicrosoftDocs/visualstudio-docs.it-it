---
title: Panoramica del protocollo Server Language | Documenti Microsoft
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de7de0ce4d37ed74a7d2291ecf2f0db98c07478b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="language-server-protocol"></a>Protocollo di lingua del Server

## <a name="what-is-the-language-server-protocol"></a>Che cos'è il protocollo Server linguaggio?

Supporto di funzionalità di modifica dettagliate come origine codice auto-completamenti o **Vai a definizione** per un linguaggio di programmazione in un editor o IDE non è in genere molto complessa e richiedere tempo. In genere richiede la scrittura di un modello di dominio (uno scanner, un parser, un controllo di tipo, un generatore e altro ancora) nel linguaggio di programmazione dell'editor o IDE. Ad esempio, il plug-in Eclipse GDTTO, che fornisce il supporto per C/C++ nell'IDE di Eclipse è scritto in linguaggio poiché l'IDE di Eclipse stesso è scritto in linguaggio. Seguendo questo approccio, comporterebbe l'implementazione di un modello di dominio di C/C++ in TypeScript per Visual Studio Code e un modello di dominio separati in c# per Visual Studio.

Creazione di modelli di dominio specifici della lingua sono inoltre molto più semplice se uno strumento di sviluppo può riutilizzare librerie specifiche della lingua esistenti. Tuttavia, queste librerie sono in genere implementate nel linguaggio di programmazione stesso (ad esempio, C/C++ dominio appropriato modelli vengono implementati in C/C++). Integrazione di una libreria di C/C++ in un editor di TypeScript è tecnicamente possibile ma difficili da eseguire.

### <a name="language-servers"></a>Server di linguaggio

Un altro approccio consiste nell'eseguire la libreria in un processo e usano la comunicazione tra processo per comunicare ad esso. I messaggi inviati e viceversa formano un protocollo. Il protocollo server language (LSP) è il prodotto di standardizzazione dei messaggi scambiati tra uno strumento di sviluppo e un processo del server di linguaggio. Utilizzo di server language o demons non è un concetto nuovo o novel. Editor quali Vim ed Emacs sono stati in questo modo per un certo tempo fornire il supporto di semantica di completamento automatico. Lo scopo del LSP era per semplificare questi tipi di integrazioni e forniscono un framework utile per l'esposizione di funzionalità del linguaggio per una varietà di strumenti.

La disponibilità di un protocollo comune consente l'integrazione di funzionalità del linguaggio di programmazione in uno strumento di sviluppo con la massima semplicità riutilizzando un'implementazione esistente del modello di dominio del linguaggio. Un linguaggio server back-end può essere scritta in PHP, Python o Java e il LSP permette di essere facilmente integrato in un'ampia gamma di strumenti. Il protocollo viene utilizzato a un livello di astrazione comune in modo che uno strumento può offrire servizi di linguaggio completo senza dover comprendere appieno le sfumature specifiche per il modello di dominio sottostante.

## <a name="how-work-on-the-lsp-started"></a>Funzionamento in Layered Service Provider di avvio

Ora è stato migliorato il LSP e oggi si trova alla versione 3.0. Viene avviato quando il concetto di un server di lingua è stato selezionato dal OmniSharp per fornire le funzionalità avanzate di modificare per c#. Inizialmente, OmniSharp utilizzato il protocollo HTTP con un payload JSON e nell'editor diverse tra cui è stato integrato [codice di Visual Studio](https://code.visualstudio.com).

Intorno all'ora, Microsoft iniziato a lavorare su un server di linguaggio TypeScript, con il concetto di supportare TypeScript negli editor Emacs e testo Sublime. In questa implementazione, un editor comunica attraverso stdin/stdout con il processo server TypeScript e Usa un payload JSON ispirata il protocollo di debugger V8 per richieste e risposte. Il server di TypeScript è stato integrato nel plug-in Sublime TypeScript e il codice di Visual Studio per la modifica di TypeScript RTF.

Dopo l'integrazione di due server lingua diversa, il team di Visual Studio Code è iniziato a esplorare un protocollo server linguaggio comune per gli editor e IDE. Un protocollo comune consente a un provider del linguaggio creare un server singolo linguaggio che può essere utilizzato da diversi IDE. Un consumer di server di linguaggio dovrà implementare solo il lato client del protocollo una sola volta. Ciò comporta una situazione vincenti per il provider del linguaggio e il consumer di linguaggio.

Il protocollo di lingua server avviato con il protocollo utilizzato dal server di TypeScript, espanderlo con altre funzionalità del linguaggio ispirata API del linguaggio di Visual Studio Code. Il protocollo viene eseguito con RPC JSON per la chiamata remota a causa di sua semplicità e librerie esistenti.

Visual Studio un file di codice il protocollo mediante l'implementazione di più server di linguaggio linter che risponde alle richieste da lint (analisi) un prototipo di team e restituisce un set di errori e avvisi rilevati. L'obiettivo era lint un file come le modifiche dell'utente in un documento, il che significa che non vi siano molte richieste linting durante una sessione dell'editor. Questa soluzione era sensata per mantenere un server di backup e in esecuzione in modo che un nuovo processo linting non sono necessarie per l'avvio per ogni modifica utente. Sono stati implementati diversi server linter, tra cui Visual Studio Code ESLint e TSLint estensioni. Questi due server linter sono sia implementato in TypeScript/JavaScript ed eseguire in Node.js. Condividono una libreria che implementa la parte di client e server del protocollo.

## <a name="how-the-lsp-works"></a>Funzionamento di LSP

Un server di linguaggio viene eseguito in un processo e strumenti come Visual Studio o Visual Studio Code comunicano con il server utilizzando il protocollo di linguaggio RPC JSON. Un altro vantaggio del server di linguaggio opera in un processo dedicato è che vengono evitati i problemi di prestazioni relativi a un modello di processo singolo. Il canale di trasporto effettivo può essere stdio, sockets, named pipe o nodo ipc se sia il client e server vengono scritte in Node.js.

Di seguito è un esempio di modalità di comunicazione durante una routine di uno strumento e un server in lingua sessione di modifica:

![diagramma di flusso LSP](media/lsp-flow-diagram.png)

* **L'utente apre un file (definito da un documento) nello strumento**: lo strumento di notifica al server linguaggio che si apre un documento (' textDocument/didOpen'). In futuro la veridicità sul contenuto del documento non è più nel file system ma mantenuti dallo strumento in memoria.

* **Le modifiche apportate dall'utente**: lo strumento di notifica al server sulla modifica del documento (' textDocument/didChange') e le informazioni semantiche del programma viene aggiornate dal server di linguaggio. Come in questo caso, il server di linguaggio analizza le informazioni e invia una notifica lo strumento con la presenza di errori e avvisi (' textDocument/publishDiagnostics').

* **L'utente esegue "Vai a definizione" su un simbolo nell'editor**: lo strumento invia una richiesta di ' textDocument/definizione' con due parametri: (1) l'URI del documento e (2) la posizione del testo da in viaggio alla richiesta di definizione è stata avviata nel server. Il server risponde con l'URI del documento e la posizione della definizione del simbolo all'interno del documento.

* **L'utente chiude il documento (file)**: viene inviata una notifica di ' textDocument/didClose' dallo strumento, informare il server di linguaggio che il documento è ora non è più in memoria e che il contenuto corrente è ora aggiornato nel file system.

Questo esempio viene illustrato come il protocollo comunica con il server di lingua a livello di funzionalità dell'editor quali "Vai a definizione", "Trova tutti i riferimenti". I tipi di dati utilizzati dal protocollo sono editor o IDE 'tipi di dati' come documento di testo aperto e la posizione del cursore. I tipi di dati non sono al livello di un modello di programmazione Java dominio che fornisce in genere strutture ad albero sintattico astratto e simboli di compilazione (ad esempio, tipi risolti, spazi dei nomi,...). Questa operazione semplifica notevolmente il protocollo.

Ora si esaminerà la richiesta ' textDocument/definizione' in modo più dettagliato. Di seguito sono riportati i payload che rientrano tra lo strumento di client e il server di lingua per la richiesta "Vai a definizione" in un documento di C++.

Si tratta della richiesta:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Questa è la risposta:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

In retrospettiva, che descrive i tipi di dati a livello dell'editor anziché a livello del modello di linguaggio di programmazione è uno dei motivi per la riuscita del protocollo server language. È molto più semplice standardizzare un URI del documento di testo o una posizione del cursore confrontato con la standardizzazione dei simboli di struttura ad albero e del compilatore un sintattico astratto tra diversi linguaggi di programmazione.

Quando un utente sta utilizzando diversi linguaggi, Visual Studio Code inizia in genere un server di lingua per ogni linguaggio di programmazione. Nell'esempio seguente viene illustrata una sessione in cui l'utente utilizza per i file Java e SASS.

![Java e sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funzionalità

Non tutti i server lingua può supportare tutte le funzionalità definite dal protocollo. Pertanto, il client e server annuncia il set di funzionalità supportata tramite 'funzionalità'. Ad esempio, un server di notifica che in grado di gestire la richiesta ' textDocument/definizione', ma che non può gestire la richiesta di 'area di lavoro/simbolo'. Analogamente, i client possono annunciare che sono in grado di fornire ' per salvare' notifiche prima di salvata un documento, in modo che un server è possibile calcolare le modifiche di testuale per formattare automaticamente il documento modificato.

## <a name="integrating-a-language-server"></a>Integrazione di un server di linguaggio

L'integrazione effettiva di un server di lingua in un particolare strumento non è definito dal protocollo del server di lingua e da sinistra a implementatori di strumento. Alcuni strumenti di integrano in modo generico server language con un'estensione che è possibile avviare e comunicare con qualsiasi tipo di server in lingua. Altri, ad esempio di codice di Visual Studio, creare un'estensione personalizzata per ogni server di lingua, in modo che un'estensione è ancora in grado di fornire alcune funzionalità del linguaggio personalizzato.

Per semplificare l'implementazione di linguaggio server e client, sono disponibili librerie o SDK per le parti di client e server. Queste librerie sono disponibili per diverse lingue. Ad esempio, è un [modulo di npm client language](https://www.npmjs.com/package/vscode-languageclient) per facilitare l'integrazione di un server di lingua in un'estensione di Visual Studio Code e un altro [modulo di npm server language](https://www.npmjs.com/package/vscode-languageserver) per scrivere un server di linguaggio tramite Node.js. Questo è il numero corrente [elenco](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) delle librerie di supporto.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Tramite il protocollo Server linguaggio in Visual Studio

* [Aggiunta di un'estensione di linguaggio Server protocollo](adding-an-lsp-extension.md) -informazioni sull'integrazione di un server di linguaggio in Visual Studio.
