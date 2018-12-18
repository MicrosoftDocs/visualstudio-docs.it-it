---
title: Identificazione e personalizzazione dei tasti di scelta rapida in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7258a1ba99764fa7af7ce73874f447db99b8b168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identificazione e personalizzazione dei tasti di scelta rapida in Visual Studio

È possibile identificare i tasti di scelta rapida per i comandi di Visual Studio, personalizzarli ed esportarli per consentirne l'utilizzo ad altri utenti. Molti tasti di scelta rapida richiamano sempre gli stessi comandi, ma il comportamento di un tasto può variare in base alle condizioni indicate di seguito.

- Impostazioni di ambiente predefinite scelte alla prima esecuzione di Visual Studio, ad esempio Sviluppo generale o Visual C#).

- Se è stato personalizzato il comportamento del tasto di scelta rapida.

- Contesto attivo quando si seleziona il tasto di scelta rapida. Ad esempio, il tasto di scelta rapida F2 richiama il comando Edit.EditCell se si utilizza Progettazione impostazioni e il comando File.Rename se si utilizza Team Explorer.

Indipendentemente dalle impostazioni, dalla personalizzazione e dal contesto, è possibile trovare e modificare un tasto di scelta rapida nella finestra di dialogo **Opzioni**. È inoltre possibile cercare i tasti di scelta rapida predefiniti per decine e decine di comandi in [Tasti di scelta rapida predefiniti per i comandi utilizzati di frequente](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) e in [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md) è disponibile un elenco completo di tutti i tasti di scelta rapida predefiniti (basati su Impostazioni generali per lo sviluppo).

Se un tasto di scelta rapida viene assegnato a un comando nel contesto globale e a nessun altro contesto, richiamerà sempre il comando in questione. Un tasto di scelta rapida può tuttavia essere assegnato a un comando nel contesto globale e a un altro in un contesto specifico. Se si utilizza tale tasto di scelta rapida nel contesto specifico, richiama il comando per il contesto specifico, non il contesto globale.

> [!NOTE]
> In base alle impostazioni e all'edizione di Visual Studio, i nomi e le pozioni dei comandi dei menu e le opzioni visualizzate nelle finestre di dialogo possono variare. Questo argomento è basato su **Impostazioni generali per lo sviluppo**.

## <a name="identifying-a-keyboard-shortcut"></a>Identificazione di un tasto di scelta rapida

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

2. Espandere **Ambiente**, quindi scegliere **Tastiera**.

   ![Visualizzare i tasti di scelta rapida nella finestra di dialogo Opzioni](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. Nella casella **Mostra comandi contenenti** immettere il nome del comando intero o parziale, senza spazi.

   Sono ad esempio disponibili comandi per `solutionexplorer`.

4. Scegliere il comando corretto nell'elenco.

    Ad esempio, è possibile scegliere **View.SolutionExplorer**.

5. Se al comando è associato un tasto di scelta rapida, verrà visualizzato nell'elenco **Tasti di scelta rapida per comando selezionato**.

   ![Visualizzare un tasto di scelta rapida per un comando specifico](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a>Personalizzazione di un tasto di scelta rapida

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

2. Espandere la cartella **Ambiente** e scegliere **Tastiera**.

3. Facoltativo: filtrare l'elenco di comandi immettendo il nome del comando in tutto o in parte, senza spazi, nella casella **Mostra comandi contenenti**.

4. Nell'elenco scegliere il comando a cui si desidera assegnare un tasto di scelta rapida.

Nell'elenco **Usa nuova combinazione in** scegliere l'area di funzionalità in cui verrà usato il tasto di scelta rapida.

    For example, you can choose **Global** if you want the shortcut to work in all contexts. You can use any shortcut that isn't mapped (as Global) in another editor. Otherwise, the editor overrides the shortcut.

    > [!NOTE]
    > You can't assign the following keys as part of a keyboard shortcut in **Global**: Print Scrn/Sys Rq, Scroll Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, the Windows logo key, the Application key, any of the Arrow keys, or Enter; Num Lock, Delete, or Clear on the numeric keypad; the Ctrl+Alt+Delete key combination.

6. Nella casella **Premi tasti di scelta rapida** immettere il tasto di scelta rapida che si vuole usare.

    > [!NOTE]
    > È possibile creare un tasto di scelta rapida che combina una lettera e il tasto ALT, il tasto CTRL oppure entrambi. È inoltre possibile creare un tasto di scelta rapida che combina il tasto MAIUSC e una lettera e il tasto ALT, il tasto CTRL oppure entrambi.

     Se un tasto di scelta rapida è già assegnato a un altro comando, verrà visualizzato nella casella **Combinazione già utilizzata da**. In tal caso, premere il tasto BACKSPACE per eliminare il tasto di scelta rapida prima di provarne un altro.

    ![Specificare un tasto di scelta rapida diverso per un comando](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Scegliere il pulsante **Assegna**.

    > [!NOTE]
    > Se si specifica un tasto di scelta rapida diverso per un comando, scegliere il pulsante **Assegna** e quindi il pulsante **Annulla**. La finestra di dialogo si chiude, ma la modifica non viene ripristinata.

## <a name="sharing-custom-keyboard-shortcuts"></a>Condivisione di tasti di scelta rapida comuni

È possibile condividere i tasti di scelta rapida personalizzati esportandoli in un file e quindi fornendo il file ad altri utenti in modo che possano importare i dati.

### <a name="to-export-only-keyboard-shortcuts"></a>Per esportare solo i tasti di scelta rapida

1. Nella barra dei menu scegliere **Strumenti**, **Importa/Esporta impostazioni**.

2. Scegliere **Esporta le impostazioni di ambiente selezionate**, quindi fare clic sul pulsante **Avanti**.

3. In **Quali impostazioni si desidera esportare?** deselezionare la casella di controllo **Tutte le impostazioni**, espandere **Opzioni** e quindi **Ambiente**.

4. Selezionare la casella di controllo **Tastiera**, quindi scegliere il pulsante **Avanti**.

    ![Esportare solo i tasti di scelta rapida personalizzati](../ide/media/exportshortcuts.png "ExportShortcuts")

5. Nelle caselle **Assegnare un nome al file di impostazioni?** e **Archivia il file di impostazioni in questa directory** lasciare i valori predefiniti o specificare valori diversi e quindi scegliere il pulsante **Fine**.

    Per impostazione predefinita, i tasti di scelta rapida vengono salvati in un file nella cartella %USERPROFILE%\Documents\Visual Studio 2017\Settings. Il nome del file riflette la data in cui sono state esportate le impostazioni e l'estensione è .vssettings.

### <a name="to-import-only-keyboard-shortcuts"></a>Per importare solo i tasti di scelta rapida

1. Nella barra dei menu scegliere **Strumenti**, **Importa/Esporta impostazioni**.

2. Selezionare il pulsante di opzione **Importa le impostazioni di ambiente selezionate**, quindi fare clic sul pulsante **Avanti**.

3. Scegliere il pulsante di opzione **No, importa soltanto le nuove impostazioni, sovrascrivendo le impostazioni correnti**, quindi il pulsante **Avanti**.

4. In **Impostazioni personali** scegliere il file contenente i tasti di scelta rapida da importare o scegliere il pulsante **Sfoglia** per individuare il file corretto.

5. Fare clic su **Avanti**.

6.  In **Quali impostazioni si desidera importare?** deselezionare la casella di controllo **Tutte le impostazioni**, espandere **Opzioni**, quindi **Ambiente**.

7. Selezionare la casella di controllo **Tastiera**, quindi scegliere il pulsante **Fine**.

    ![Importare solo i tasti di scelta rapida personalizzati](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Vedere anche

[Accessibility Features of Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md) (Funzionalità di accessibilità di Visual Studio)