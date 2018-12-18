---
title: Individuare e usare altre estensioni di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f3057ae7cf987c19e87329894249031b3af29806
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="find-and-use-visual-studio-extensions"></a>Individuare e usare altre estensioni di Visual Studio

Le estensioni di Visual Studio sono pacchetti di codice eseguiti in Visual Studio che forniscono funzionalità di Visual Studio nuove o migliorate. Altre informazioni sulle estensioni di Visual Studio sono disponibili qui: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

È possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per installare estensioni ed esempi di Visual Studio da siti Web e da altri percorsi e quindi abilitarli, disabilitarli, aggiornarli o disinstallarli (**Strumenti / Estensioni e aggiornamenti**oppure digitare **Estensioni** nella finestra **Avvio veloce** ). Nella finestra di dialogo vengono visualizzati anche gli aggiornamenti per le estensioni e gli esempi installati. È anche possibile scaricare estensioni da siti Web od ottenerle da altri sviluppatori.

> [!NOTE]
> A partire da Visual Studio 2015, le estensioni ospitate in Visual Studio Marketplace vengono aggiornate automaticamente. È possibile modificare questa impostazione tramite la finestra di dialogo **Estensioni e aggiornamenti** .  Per informazioni dettagliate, vedere la sezione **Aggiornamenti automatici delle estensioni** più avanti.

## <a name="finding-visual-studio-extensions"></a>Ricerca delle estensioni di Visual Studio

È possibile installare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Le estensioni possono essere controlli, esempi, modelli, strumenti o altri componenti che aggiungono funzionalità a Visual Studio. In Visual Studio sono supportate estensioni nel formato di pacchetto VSIX. Queste includono modelli di progetto, modelli di elemento, elementi di **Casella degli strumenti** componenti MEF (Managed Extension Framework) e VSPackage. È anche possibile scaricare le estensioni basate su MSI, ma la finestra di dialogo **Estensioni e aggiornamenti** non consente di abilitarle o disabilitarle. Visual Studio Marketplace contiene estensioni VSIX e MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Installazione e disinstallazione delle estensioni di Visual Studio

Nella sezione relativa a **estensioni e aggiornamenti**trovare l'estensione che si vuole installare (se si conosce il nome dell'estensione o parte di esso, è possibile eseguire la ricerca nella finestra di**ricerca**). Fare clic su **Download**.  L'estensione verrà pianificata per l'installazione. L'estensione verrà installata dopo la chiusura di tutte le istanze di Visual Studio.

Se si tenta di installare un'estensione con dipendenze, il programma di installazione verifica se siano già installate. Se non sono installate, nella finestra di dialogo **Estensioni e aggiornamenti** verranno elencate tutte le dipendenze che devono essere installate prima dell'estensione.

Se si desidera interrompere l'utilizzo di un'estensione, è possibile disabilitarla o disinstallarla. Disabilitandola, un'estensione rimarrà installata ma non caricata. È possibile disabilitare solo le estensioni VSIX; le estensioni installate usando un file MSI possono solo essere disinstallate. Trovare l'estensione e fare clic su **Disinstalla** o **Disabilita**. Per scaricare un'estensione disabilitata, è necessario riavviare Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Estensioni amministrative e per utente

La maggior parte delle estensioni sono per utente e sono installate nella cartella **%LocalAppData%\Microsoft\VisualStudio\\<Versione Visual Studio\>\Extensions\\**. Alcune estensioni sono amministrative e vengono installate nel percorso **\<Cartella di installazione Visual Studio>\Common7\IDE\Extensions\\**.

Per proteggere il sistema da estensioni che possono contenere errori o codice dannoso, è possibile limitare il caricamento delle estensioni per utente nei soli in casi in cui Visual Studio sia in esecuzione con autorizzazioni utente normali. Ciò significa che le estensioni per utente sono disabilitate quando Visual Studio viene eseguito con autorizzazioni utente amministrative. A questo scopo, passare alla pagina delle opzioni **Estensioni e aggiornamenti** (**Strumenti / Opzioni**, **Ambiente**, **Estensioni e aggiornamenti**oppure digitare **Estensione** nella finestra **Avvio veloce** ). Deselezionare la casella di controllo **Carica estensioni per utente se eseguite come amministratore** , quindi riavviare Visual Studio.

## <a name="automatic-extension-updates"></a>Aggiornamenti automatici delle estensioni

Le estensioni per utente vengono aggiornate automaticamente quando è disponibile una nuova versione per Visual Studio Marketplace.  La nuova versione dell'estensione viene rilevata e installata in background e viene quindi eseguita al successivo riavvio di Visual Studio.

Solo le estensioni per utente possono essere aggiornate automaticamente.  Le estensioni amministrative installate per tutti gli utenti non vengono aggiornate ed è necessario installare manualmente le nuove versioni tramite il nodo **Aggiornamenti** della finestra di dialogo **Estensioni e aggiornamenti**. È possibile visualizzare le estensioni che verranno aggiornate automaticamente nel riquadro dei dettagli dell'estensione nella finestra di dialogo **Estensioni e aggiornamenti**.

Se si desidera disabilitare gli aggiornamenti automatici, è possibile disabilitare la funzionalità per tutte le estensioni o solo per estensioni specifiche.

- Per disabilitare gli aggiornamenti automatici per tutte le estensioni, selezionare il collegamento **Modifica le impostazioni di estensioni e aggiornamenti** nella finestra di dialogo **Estensioni e aggiornamenti** e deselezionare **Aggiorna automaticamente le estensioni**.

- Per disabilitare gli aggiornamenti automatici per un'estensione specifica, deselezionare l'opzione **Aggiorna automaticamente questa estensione** nel riquadro dei dettagli dell'estensione sul lato destro della finestra di dialogo **Estensioni e aggiornamenti**.

> [!NOTE]
> A partire da Visual Studio 2015 Update 2, è possibile specificare in **Strumenti / Opzioni / Ambiente / Estensioni e aggiornamenti** se gli aggiornamenti automatici devono essere installati per le estensioni per utente, per tutte le estensioni utente o entrambe le opzioni (impostazione predefinita).

## <a name="extension-crashunresponsiveness-notifications"></a>Notifiche di arresto anomalo o blocco di un'estensione

Una novità di **Visual Studio 2017 versione 15.3** prevede che Visual Studio notifichi l'utente se sospetta che un'estensione è stata coinvolta in un arresto anomalo del sistema durante una sessione precedente. Quando Visual Studio subisce un arresto anomalo del sistema, memorizza lo stack dell'eccezione. Al successivo avvio di Visual Studio, viene esaminato lo stack, a partire dal nodo foglia e procedendo verso la base. Se Visual Studio determina che un frame appartiene a un modulo che fa parte di un'estensione installata e abilitata, visualizza una notifica.

Un'altra novità di **Visual Studio 2017 versione 15.6** prevede che Visual Studio invii una notifica anche se sospetta che un'estensione sia la causa di un blocco dell'interfaccia utente.

Quando queste notifiche vengono visualizzate, è possibile ignorare la notifica o eseguire una delle azioni seguenti:

- Scegliere **Disabilita questa estensione**. Visual Studio disabilita l'estensione e comunica se è necessario riavviare il sistema per rendere effettiva la disabilitazione. Se lo si desidera è possibile riabilitare l'estensione nella finestra di dialogo **Estensioni e aggiornamenti**.

- Scegliere **Non visualizzare più questo messaggio**.
  - Se la notifica riguarda un arresto anomalo in una sessione precedente, Visual Studio non visualizzerà più una notifica quando si verifica un arresto anomalo associato a questa estensione. Visual Studio visualizzerà comunque le notifiche in caso di blocco associabile all'estensione o per arresti anomali o blocchi che possono essere associati ad altre estensioni.
  - Se la notifica riguarda un blocco, l'IDE non visualizzerà più una notifica quando questa estensione è associata al blocco. Visual Studio visualizzerà comunque notifiche correlate all'arresto anomalo per questa estensione e correlate ad arresti anomali o blocchi per altre estensioni.

- Scegliere **Altre informazioni** per visualizzare questa pagina.

- Scegliere il pulsante **X** al termine della notifica per ignorarla. Verrà visualizzata una nuova notifica per le istanze future dell'estensione associata a un arresto anomalo o al blocco dell'interfaccia utente.

> [!NOTE]
> Una notifica di blocco dell'interfaccia utente o di arresto anomalo significa solo che uno dei moduli dell'estensione si trovava nello stack quando si è verificato il blocco dell'interfaccia utente o l'arresto anomalo. Ciò non significa necessariamente che l'estensione stessa sia la causa. È possibile che l'estensione abbia chiamato codice che fa parte di Visual Studio, che a sua volta ha causato il blocco dell'interfaccia utente o l'arresto anomalo. Tuttavia, la notifica può rivelarsi ancora utile se l'estensione che ha causato il blocco dell'interfaccia utente o l'arresto anomalo non è importante. In questo caso, la disabilitazione dell'estensione evita il blocco dell'interfaccia utente o l'arresto anomalo in futuro senza influire sulla produttività.

## <a name="sample-master-copies-and-working-copies"></a>Copie master e copie di lavoro di esempio

Quando si installa un esempio online, la soluzione viene memorizzata in due posizioni:

- Una copia di lavoro viene memorizzata nel percorso specificato nella finestra di dialogo **Nuovo progetto** .

- Una copia master separata viene memorizzata nel computer.

È possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per eseguire queste attività correlate agli esempi:

- Elencare le copie master degli esempi installati.

- Disabilitare o disinstallare la copia master di un esempio.

- Installare pacchetti di esempio, ovvero raccolte di esempi relativi a una tecnologia o una funzionalità.

- Installare singoli esempi online. A tale scopo è inoltre possibile usare la finestra di dialogo **Nuovo progetto** .

- Visualizzare notifiche di aggiornamenti quando vengono pubblicate modifiche al codice sorgente per gli esempi installati.

- Aggiornare la copia master di un esempio installato quando è disponibile una notifica di aggiornamento.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installazione senza usare la finestra di dialogo Estensioni e Aggiornamenti

Le estensioni che sono state incluse in file con estensione vsix possono essere disponibili in posizioni diverse da Visual Studio Marketplace. Benché la finestra di dialogo **Estensioni e aggiornamenti** non permetta di individuare questi file, è possibile installare un file VSIX facendovi doppio clic sopra oppure selezionandolo e quindi premendo INVIO. Quindi, è sufficiente seguire le istruzioni. Una volta installata l'estensione, sarà possibile usare la finestra di dialogo **Estensioni e aggiornamenti** per abilitarla, disabilitarla o disinstallarla.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Tipi di estensione non supportati dalla finestra di dialogo Estensioni e aggiornamenti

Visual Studio continua a supportare le estensioni installate da Microsoft Installer (MSI) ma non tramite la finestra di dialogo **Estensioni e aggiornamenti** senza modifica.

> [!TIP]
> Se un'estensione basata su MSI include un file extension.vsixmanifest, tale estensione verrà visualizzata nella finestra di dialogo **Estensioni e aggiornamenti** .
