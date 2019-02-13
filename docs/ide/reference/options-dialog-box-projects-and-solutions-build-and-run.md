---
title: Opzioni (finestra di dialogo), Progetti e soluzioni, Compila ed esegui
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2e62a0b9ece6052d222a8c228bbd7fe018b0a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954777"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Opzioni (finestra di dialogo), Progetti e soluzioni, Compila ed esegui

In questa finestra di dialogo è possibile specificare il numero massimo di progetti Visual C++ o C# che è possibile compilare allo stesso tempo, determinati comportamenti di compilazione predefiniti e alcune impostazioni del log di compilazione. Per accedere a queste opzioni selezionare **Strumenti > Opzioni**, espandere **Progetti e soluzioni** e selezionare **Compila ed esegui**.

**Numero massimo di compilazioni di progetto parallele**

Specifica il numero massimo di progetti Visual C++ e C# che è possibile compilare contemporaneamente. Per ottimizzare il processo di compilazione, il numero massimo di compilazioni di progetti in parallelo viene impostato automaticamente sul numero di CPU del computer. Il numero massimo è 32.

**Compila progetti di avvio e dipendenze solo in fase di esecuzione**

Compila solo il progetto di avvio e le relative dipendenze quando si usa il tasto F5, si seleziona il comando di menu **Debug > Avvia** o i comandi applicabili del menu **Genera**. Senza impostazioni, vengono compilati tutti i progetti e le relative dipendenze.

**Durante l'esecuzione, quando i progetti non sono aggiornati**

*Si applica solo ai progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Quando si esegue un progetto con F5 o il comando **Debug > Avvia** l'impostazione predefinita **Richiedi compilazione** visualizza un messaggio se una configurazione di progetto non è aggiornata. Selezionare **Compila sempre** per compilare il progetto ogni volta che viene eseguito. Selezionare **Non compilare mai** per eliminare tutte le compilazioni automatiche quando si esegue un progetto.

**Durante l'esecuzione, quando si verificano errori di compilazione o distribuzione**

*Si applica solo ai progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Quando si esegue un progetto con F5 o il comando **Debug > Avvia** l'impostazione predefinita **Richiedi avvio** visualizza un messaggio se un progetto deve essere eseguito anche se la compilazione non è riuscita. Selezionare **Avvia versione precedente** per avviare automaticamente l'ultima compilazione valida. In questo modo è possibile che il codice in esecuzione non corrisponda al codice sorgente. Selezionare **Non avviare** per eliminare il messaggio.

**Per nuove soluzioni utilizza il progetto selezionato come progetto di avvio**

Se questa opzione è impostata, le nuove soluzioni usano il progetto selezionato come progetto di avvio.

**Livello di dettaglio output in compilazione progetto MSBuild**

Determina la quantità di informazioni visualizzata nella finestra **Output** per la compilazione.

**Livello di dettaglio file di log di compilazione progetto MSBuild**

*Si applica solo ai progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Determina la quantità di informazioni scritta nel file di log di compilazione che si trova in \\...\\*ProjectName*\Debug\\*ProjectName*.log.

## <a name="see-also"></a>Vedere anche

- [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)
- [Finestra di dialogo Opzioni, Progetti e soluzioni](projects-and-solutions-options-dialog-box.md)
- [Finestra di dialogo Opzioni, Progetti e soluzioni, Progetti Web](options-dialog-box-projects-and-solutions-web-projects.md)