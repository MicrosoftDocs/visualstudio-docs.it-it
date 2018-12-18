---
title: Generale, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c427752fa1b89acb2fa55afc7acd8c4535686c37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="general-environment-options-dialog-box"></a>Generale, Ambiente, finestra di dialogo Opzioni

Usare questa pagina per modificare i temi di colori, le impostazioni della barra di stato e le associazioni dell'estensione di file, tra le altre opzioni, per l'ambiente di sviluppo integrato (IDE). Per accedere alla finestra di dialogo **Opzioni**, aprire il menu **Strumenti**, scegliere **Opzioni**, aprire la cartella **Ambiente** e scegliere la pagina **Generale**. Se la pagina non viene visualizzata nell'elenco, selezionare la casella di controllo **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, aprire il menu **Strumenti** e quindi scegliere **Importa/Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="visual-experience"></a>Esperienza visiva

**Tema colori**

Scegliere il tema colori **Blu**, **Chiaro** o **Scuro** per l'IDE.

È possibile installare temi predefiniti aggiuntivi e creare temi personalizzati scaricando e installando **Visual Studio Color Theme Editor** da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Dopo avere installato questo strumento, i temi colori aggiuntivi vengono visualizzati nella casella di riepilogo Tema colori.

**Applicare lo stile Tutte Iniziali Maiuscole nella barra dei menu**

Per impostazione predefinita, i menu sono visualizzati con lo stile **Tutte Iniziali Maiuscole**. Deselezionare questa opzione per impostarli su **TUTTO MAIUSCOLE**.

**Regola automaticamente esperienza visiva in base alle prestazioni del client**

Specifica se Visual Studio imposta automaticamente la regolazione dell'esperienza visiva o la regolazione viene impostata in modo esplicito dall'utente. Questa regolazione può modificare la visualizzazione di colori da gradienti a colori uniformi o può limitare l'uso di animazioni nei menu o finestre a comparsa.

**Abilita esperienza visiva dettagliata del client**

Consente l'esperienza visiva completa di Visual Studio, inclusi i gradienti e le animazioni. Deselezionare questa opzione se si usano Connessioni desktop remoto o schede grafiche obsolete, perché le prestazioni di queste funzionalità potrebbero risultare compromesse. Questa opzione è disponibile solo se si deseleziona l'opzione **Regola automaticamente esperienza visiva in base alle prestazioni del client**.

**Usa accelerazione grafica hardware se disponibile**

Usa l'accelerazione grafica hardware, se disponibile, piuttosto che l'accelerazione software.

## <a name="other"></a>Altro

**Elementi nel menu Finestra**  Consente di personalizzare il numero di finestre visualizzate nell'elenco Finestre accessibile dal menu **Finestra**. Digitare un numero compreso tra 1 e 24. Per impostazione predefinita, il numero è 10.

**Elementi negli elenchi degli ultimi file usati** Consente di personalizzare il numero dei file e dei progetti usati più di recente visualizzati nel menu **File**. Digitare un numero compreso tra 1 e 24. Per impostazione predefinita, il numero è 10. Questa funzionalità offre un modo semplice per recuperare progetti e file usati di recente.

**Mostra barra di stato** Consente di visualizzare la barra di stato. Nella barra di stato, posizionata nella parte inferiore della finestra dell'IDE, sono visualizzate le informazioni sullo stato delle operazioni in corso.

**Chiudi ha effetto solo sulla finestra degli strumenti attiva** Consente di specificare che quando si fa clic sul pulsante **Chiudi** deve essere chiusa solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è selezionata per impostazione predefinita.

**Nascondi automaticamente ha effetto solo sulla finestra degli strumenti attiva** Consente di specificare che se si fa clic sul pulsante **Nascondi automaticamente** deve essere nascosta automaticamente solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è deselezionata per impostazione predefinita.

## <a name="see-also"></a>Vedere anche

[Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)
[Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)