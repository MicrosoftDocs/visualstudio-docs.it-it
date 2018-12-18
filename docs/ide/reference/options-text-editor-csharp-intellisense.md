---
title: Opzioni, Editor di testo, C#, IntelliSense | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 37640cd6bd2928a2e2261afb3ed9e859830d0225
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-c-intellisense"></a>Opzioni, Editor di testo, C#, IntelliSense

Usare la pagina delle opzioni **IntelliSense** per modificare le impostazioni che hanno effetto sul comportamento di IntelliSense per C#. Per accedere a questa pagina di opzioni, scegliere **Strumenti** > **Opzioni** e quindi scegliere **Editor di testo** > **C#** > **IntelliSense**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

La pagina delle opzioni **IntelliSense** include le opzioni seguenti:

## <a name="completion-lists"></a>Elenchi di completamento

- Mostra elenco di completamento dopo la digitazione di un carattere*

   Quando questa opzione è selezionata, IntelliSense visualizza automaticamente l'elenco di completamento quando si inizia a digitare. Quando questa opzione non è selezionata, il completamento di IntelliSense è ancora disponibile tramite il menu **IntelliSense** o premendo **CTRL**+**BARRA SPAZIATRICE**.

- Mostra elenco di completamento dopo l'eliminazione di un carattere

- Evidenzia le parti corrispondenti di voci dell'elenco di completamento

- Mostra filtri per le voci di completamento

- Mostra suggerimenti per nomi

### <a name="snippets-behavior"></a>Comportamento dei frammenti

- Non includere mai i frammenti

   Quando questa opzione è selezionata, IntelliSense non aggiunge mai gli alias per i frammenti di codice C# all'elenco di completamento.

- Includi sempre i frammenti

   Quando questa opzione è selezionata, IntelliSense aggiunge gli alias per i frammenti di codice C# all'elenco di completamento. Se l'alias del frammento di codice corrisponde a una parola chiave, ad esempio [class](/dotnet/csharp/language-reference/keywords/class), la parola chiave viene sostituita dal collegamento. Per altre informazioni, vedere [Frammenti di codice C#](../../ide/visual-csharp-code-snippets.md).

- Includi i frammenti quando si digita ?+TAB dopo un identificatore

   Quando questa opzione è selezionata, IntelliSense aggiunge gli alias per i frammenti di codice C# all'elenco di completamento quando si preme **?**+**TAB** dopo un identificatore.

### <a name="enter-key-behavior"></a>Comportamento del tasto INVIO

- Non aggiungere mai una nuova riga dopo INVIO

   Specifica che non viene mai aggiunta automaticamente una nuova riga dopo aver selezionato un elemento nell'elenco di completamento e premuto **INVIO**.

- Aggiungi una nuova riga dopo INVIO alla fine della parola digitata

   Specifica che se si digitano tutti i caratteri di una voce dell'elenco di completamento e quindi si preme **INVIO**, viene aggiunta automaticamente una nuova riga e il cursore si sposta nella nuova riga.

   Ad esempio, se si digita `else` e quindi si preme **INVIO**, nell'editor viene visualizzato quanto segue:

   `else`

   `|` (posizione del cursore)

   Tuttavia, se si digita solo `el` e quindi si preme **INVIO**, nell'editor viene visualizzato quanto segue:

   `else|` (posizione del cursore)

- Aggiungi sempre una nuova riga dopo INVIO

   Specifica che se si digita *qualsiasi* carattere di una voce dell'elenco di completamento e quindi si preme **INVIO**, viene creata automaticamente una nuova riga e il cursore si sposta nella nuova riga.

## <a name="see-also"></a>Vedere anche

[Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)  
[Utilizzo di IntelliSense](../../ide/using-intellisense.md)