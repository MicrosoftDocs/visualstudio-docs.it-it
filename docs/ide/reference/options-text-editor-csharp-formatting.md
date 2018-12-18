---
title: Opzioni, Editor di testo, C#, Formattazione | Microsoft Docs
ms.date: 02/09/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: db7140248818cc92f95150e7a368fa0f71d1d010
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-c-formatting"></a>Opzioni, Editor di testo, C#, Formattazione

Usare la pagina di opzioni **Formattazione** per impostare le opzioni di formattazione del codice nell'editor del codice. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **C#**  >  **Stile codice** > **Formattazione**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-settings"></a>Impostazioni generali

Le impostazioni generali hanno effetto sulla modalità con la quale l'editor del codice applica le opzioni di formattazione al codice.

## <a name="uielement-list"></a>Elenco UIElement

|Label|Descrizione|
|-----------|-----------------|
|**Formatta automaticamente durante la digitazione**|Quando questa opzione è deselezionata, le opzioni **Formatta automaticamente istruzione dopo :** e **Formatta automaticamente blocco dopo }** sono disabilitate.|
|**Formatta automaticamente istruzione dopo ;**|Quando questa opzione è selezionata, le istruzioni vengono formattate al completamento in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente blocco dopo }**|Quando questa opzione è selezionata, i blocchi di codice vengono formattati in base alle opzioni di formattazione selezionate per l'editor subito dopo il completamento del blocco di codice.|
|**Formatta automaticamente dopo INVIO**|Quando questa opzione è selezionata, il testo viene formattato dopo la pressione di **INVIO**, in base alle opzioni di formattazione selezionate per l'editor.|
|**Formatta automaticamente dopo operazione Incolla**|Quando questa opzione è selezionata, il testo incollato nell'editor viene formattato in base alle opzioni di formattazione selezionate per l'editor.|

## <a name="preview-window"></a>Finestra di anteprima

I riquadri delle opzioni **Rientro**, **Nuove righe**, **Spaziatura** e **Ritorno a capo** visualizzano una finestra di anteprima. La finestra di anteprima illustra l'effetto di ogni opzione. Per usare la finestra di anteprima, selezionare un'opzione di formattazione. La finestra di anteprima illustra un esempio dell'opzione selezionata. Quando si modifica un'impostazione selezionando un pulsante di opzione o una casella di controllo, la finestra di anteprima viene aggiornata per mostrare l'effetto della nuova impostazione.

## <a name="remarks"></a>Note

Le opzioni di rientro nelle pagine **Tabulazioni** per ogni linguaggio determinano solo il punto in cui l'editor del codice posiziona il cursore quando si preme **INVIO** alla fine di una riga. Le opzioni di rientro in **Formattazione** si applicano quando il codice viene formattato automaticamente, ad esempio quando si incolla codice nel file ed è selezionata l'opzione **Formatta automaticamente dopo operazione Incolla** o quando il blocco da formattare viene digitato manualmente.

## <a name="see-also"></a>Vedere anche

[Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)
