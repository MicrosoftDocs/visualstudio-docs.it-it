---
title: Usare i parametri della riga di comando per installare Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/17/2018
ms.reviewer: tims
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 348634224d76b3a7f51246f2be49720173ab8cd3
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Usare i parametri della riga di comando per installare Visual Studio 2017
Quando si installa Visual Studio 2017 da un prompt dei comandi, è possibile usare diversi parametri della riga di comando per controllare o personalizzare l'installazione. Dalla riga di comando è possibile eseguire le azioni seguenti:

- Avviare l'installazione con determinate opzioni preselezionate.
- Automatizzare il processo di installazione.
- Creare una cache (layout) dei file di installazione per riutilizzarli in seguito.

Insieme alle opzioni della riga di comando viene usato il programma di bootstrap dell'installazione, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Il programma di avvio automatico è il primo eseguibile che viene avviato quando si esegue il download dal sito di Visual Studio. Usare i collegamenti seguenti per accedere direttamente al programma di bootstrap della versione più recente per l'edizione del prodotto da installare:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Elenco dei parametri della riga di comando  
 Per i parametri della riga di comando di Visual Studio non viene fatta distinzione tra maiuscole e minuscole.

> Sintassi: `vs_enterprise.exe [command] <options>...`

(Sostituire `vs_enterprise.exe` con l'edizione del prodotto da installare.

>[!TIP]
> Per altri esempi di come usare la riga di comando per installare Visual Studio 2017, vedere la pagina [Esempi di parametri della riga di comando](command-line-parameter-examples.md).)

| **Comando** | **Descrizione** |
| ----------------------- | --------------- |
| (vuoto) | Installa il prodotto. |
| `modify` | Modifica un prodotto installato. |
| `update` | Aggiorna un prodotto installato. |
| `repair` | Ripristina un prodotto installato. |
| `uninstall` | Disinstalla un prodotto installato. |

| **Opzione di installazione** | **Descrizione** |
| ----------------------- | --------------- |
| `--installPath <dir>` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, è **facoltativa** e si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, è **obbligatoria** e si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| `--addProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da installare nel prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Se non è presente, l'installazione usa le impostazioni locali del computer. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--removeProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da rimuovere dal prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--remove <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da rimuovere. Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--in <path>` | **Facoltativa**: URI o percorso di un file di risposta.  |
| `--all` | **Facoltativa**: se devono essere installati tutti i carichi di lavoro e i componenti per un prodotto. |
| `--allWorkloads` | **Facoltativa**: installa tutti i carichi di lavoro e i componenti, nessun componente consigliato o facoltativo. |
| `--includeRecommended` | **Facoltativa**: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativa**: include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Facoltativa**: consente di non visualizzare alcuna interfaccia utente durante l'installazione. |
| `--passive, -p` | **Facoltativa**: consente di visualizzare l'interfaccia utente, senza richiedere alcuna interazione da parte dell'utente. |
| `--norestart` | **Facoltativa**: se presente, i comandi con `--passive` o `--quiet` non riavviano automaticamente il computer (se richiesto).  Viene ignorata se non vengono specificate né `--passive` né `--quiet`.  |
| `--nickname <name>` | **Facoltativa**: definisce il nome alternativo da assegnare a un prodotto installato. La lunghezza del nome alternativo non può superare i 10 caratteri.  |
| `--productKey` | **Facoltativa**: definisce il codice Product Key da usare per un prodotto installato. È composto da 25 caratteri alfanumerici in formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Visualizza una versione offline di questa pagina. |

> Nota: quando si specificano più carichi di lavoro e componenti, è necessario ripetere l'opzione della riga di comando `--add` o `--remove` per ogni elemento.

| **Opzioni di layout** | **Descrizione** |
| ----------------------- | --------------- |
| `--layout <dir>` | Specifica una directory per creare una cache di installazione offline. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facoltativa**: viene usata con `--layout` per preparare una cache di installazione offline con i pacchetti di risorse con le lingue specificate. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). <br/>**Nota**: se viene usato `--add`, vengono scaricati solo i carichi di lavoro e i componenti specificati (con le relative dipendenze). Se non viene specificato `--add`, vengono scaricati nel layout tutti i componenti e i carichi di lavoro.|
| `--includeRecommended` | **Facoltativa**: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativo**: include i componenti consigliati *e* facoltativi per tutti i carichi di lavoro inclusi nel layout. I carichi di lavoro sono specificati con `--add`.  |
| `--keepLayoutVersion` | **Novità in 15.3, facoltativa**: è possibile applicare le modifiche al layout senza aggiornare la versione del layout. |
| `--verify` | **Novità in 15.3, facoltativa**: è possibile verificare i contenuti di un layout.  Vengono elencati eventuali file danneggiati o mancanti. |
| `--fix` | **Novità in 15.3, facoltativa**: è possibile verificare i contenuti di un layout.  Se alcuni file risultano danneggiati o mancanti, vengono scaricati di nuovo.  Per correggere un layout, è necessario l'accesso a Internet. |
| `--clean <one or more paths to catalogs>` | **Novità in 15.3, facoltativa**: rimozione delle versioni precedenti dei componenti da un layout che è stato aggiornato a una versione più recente. |

| **Opzioni di installazione avanzate** | **Descrizione** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facoltativa**: ID del canale per l'istanza che da installare. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione `--installPath`. |
| `--channelUri <uri>` | **Facoltativa**: URI del manifesto del canale. Se non si desiderano aggiornamenti, `--channelUri` può puntare a un file inesistente, ad esempio, --channelUri C:\nonesiste.chman. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--installChannelUri <uri>` | **Facoltativa**: URI del manifesto del canale da usare per l'installazione. L'URI specificato da `--channelUri` (che deve essere specificato quando si specifica `--installChannelUri`) viene usato per rilevare gli aggiornamenti. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--installCatalogUri <uri>` | **Facoltativa**: URI del manifesto del catalogo da usare per l'installazione. Se specificato, il gestore del canale prova a scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--productId <id>` | **Facoltativa**: ID del prodotto per l'istanza che verrà installata. Prepopolata nelle condizioni di normale installazione. |
| `--wait` | **Facoltativa**: il processo attenderà fino al completamento dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| `--locale <language-locale>` | **Facoltativa**: modifica la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--cache` | **Novità di 15.2, facoltativa**: se presente, i pacchetti verranno mantenuti anche dopo l'installazione per eventuali ripristini successivi. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--nocache` | **Novità in 15.2, facoltativa**: se presente, i pacchetti vengono eliminati dopo essere stati installati o riparati. Verranno nuovamente scaricati solo se necessario ed eliminati di nuovo dopo l'uso. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Novità in 15.2, facoltativa**: se è presente, impedisce al programma di installazione di aggiornarsi quando è specificata la modalità non interattiva. Il programma di installazione non riuscirà a eseguire il comando e restituirà un codice di uscita diverso da zero se è noUpdateInstaller con modalità non interattiva quando è richiesto un aggiornamento del programma di installazione. |
| `--noWeb` | **Novità in 15.3, facoltativa**: il programma di installazione scarica ora qualsiasi contenuto che viene installato da Internet.  Tutti i contenuti installati devono essere disponibili in un layout offline.  Se nel layout mancano contenuti, il programma di installazione ha esito negativo.  Per altre informazioni, vedere [Distribuzione da un'installazione di rete](create-a-network-installation-of-visual-studio.md). |

## <a name="list-of-workload-ids-and-component-ids"></a>Elenco di ID di carichi di lavoro e ID di componenti
Per un elenco degli ID di componenti e carichi di lavoro ordinati per prodotto Visual Studio, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue
| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |
| cs-CZ | Ceco |
| de-DE | Tedesco |
| it-IT | Inglese |
| es-ES | Spagnolo |
| fr-FR | Francese |
| it-IT | Italiano |
| ja-JP | Giapponese |
| ko-KR | Coreano |
| pl-PL | Polacco |
| pt-BR | Portoghese (Brasile) |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Cinese semplificato |
| zh-TW | Cinese tradizionale |

## <a name="error-codes"></a>Codici di errore
A seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` verrà impostata su uno dei valori seguenti:

| **Valore** | **Risultato** |
| --------- | ---------- |
| 0 | L'operazione è riuscita |
| 1602 | L'operazione è stata annullata |
| 3010 | L'operazione è riuscita, ma è necessario riavviare per poter usare l'installazione |
| 5004 | L'operazione è stata annullata |
| 5007 | L'operazione è stata bloccata. Il computer non soddisfa i requisiti |
| Altro | Si è verificata una condizione di errore. Per altre informazioni, vedere i log |

Durante ogni operazione nella directory `%TEMP%` vengono generati diversi file di log che indicano lo stato di avanzamento dell'installazione. Ordinare la cartella per data e cercare i file che iniziano con `dd_bootstrapper`, `dd_client` e `dd_setup` per individuare quelli che si riferiscono rispettivamente al programma di avvio automatico, all'app del programma di installazione e al motore di installazione.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

 * [Command-line parameter examples for Visual Studio 2017 installation](command-line-parameter-examples.md) (Esempi di parametri della riga di comando per l'installazione di Visual Studio 2017)
 * [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md)
