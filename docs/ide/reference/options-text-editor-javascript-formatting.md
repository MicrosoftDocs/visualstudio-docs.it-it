---
title: Opzioni, Editor di testo, JavaScript, Formattazione
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17552294f4ce0fdfd3e78621217c4495186a365e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042816"
---
# <a name="options-text-editor-javascript-formatting"></a>Opzioni, Editor di testo, JavaScript, Formattazione
Usare la pagina **Formattazione** della finestra di dialogo **Opzioni** per impostare le opzioni di formattazione del codice nell'editor di codice. Per accedere alla pagina, nella barra dei menu scegliere **Strumenti**, **Opzioni** e quindi espandere **Editor di testo**, **JavaScript** e **Formattazione**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Formattazione automatica
 Queste opzioni determinano quando viene applicata la formattazione nella visualizzazione **Origine**.

### <a name="uielement-list"></a>Elenco UIElement

|Opzione|Description|
|------------|-----------------|
|**Formatta riga completata dopo INVIO**|Quando questa opzione è selezionata, l'editor di codice formatta automaticamente la riga quando si sceglie il tasto INVIO.|
|**Formatta istruzione completata dopo ;**|Quando questa opzione è selezionata, l'editor di codice formatta automaticamente la riga quando si sceglie il tasto punto e virgola.|
|**Format opened block on {**(Formatta blocco aperto con {)|Se questa opzione è selezionata, l'editor di codice formatta automaticamente la riga quando si sceglie il tasto parentesi graffa di apertura.|
|**Formatta blocco completato dopo }**|Quando questa opzione è selezionata, l'editor di codice formatta automaticamente la riga quando si sceglie il tasto parentesi graffa di chiusura.|
|**Formatta dopo Incolla**|Quando questa opzione è selezionata, l'editor di codice riformatta il codice incollato nell'editor. L'editor usa le regole di formattazione correntemente definite. Se questa opzione non è selezionata, l'editor usa la formattazione originale del codice incollato.|

## <a name="new-lines"></a>Nuove righe
 Queste opzioni determinano se l'editor di codice inserisce una parentesi graffa aperta per le funzioni e i blocchi di controllo in una nuova riga.

### <a name="uielement-list"></a>Elenco UIElement

|Opzione|Description|
|------------|-----------------|
|**Inserisci parentesi graffa aperta su nuova riga per le funzioni**|Quando questa opzione è selezionata, l'editor di codice sposta la parentesi graffa aperta associata a una funzione in una nuova riga.|
|**Inserisci parentesi graffa aperta su nuova riga per i blocchi di controllo**|Quando questa opzione è selezionata, l'editor di codice sposta in una nuova riga la parentesi graffa aperta associata a un blocco di controllo, ad esempio ai blocchi `if` e `while`.|

## <a name="spacing"></a>Spacing (Spaziatura)
 Queste opzioni determinano la modalità in cui vengono inseriti gli spazi nella visualizzazione **Origine**.

### <a name="uielement-list"></a>Elenco UIElement

|Opzione|Description|
|------------|-----------------|
|**Inserisci spazio dopo virgola di delimitazione**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio dopo le virgole di delimitazione.|
|**Inserisci spazio dopo punto e virgola nell'istruzione 'for'**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio dopo ogni punto e virgola nella prima riga di un ciclo `for`.|
|**Inserisci spazio prima e dopo gli operatori binari**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio prima e dopo gli operatori binari, ad esempio +, -, &&, &#124;&#124;.|
|**Inserisci spazio dopo le parole chiave nelle istruzioni del flusso di controllo**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio dopo le parole chiave JavaScript nelle istruzioni del flusso di controllo.|
|**Inserisci uno spazio dopo la parola chiave function per funzioni anonime**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio dopo la parola chiave `function` per le funzioni anonime.|
|**Inserisci uno spazio dopo le parentesi di apertura e di chiusura non vuote**|Quando questa opzione è selezionata, l'editor di codice aggiunge uno spazio dopo la parentesi di apertura e prima della parentesi di chiusura se sono presenti caratteri non vuoti all'interno delle parentesi.|

## <a name="see-also"></a>Vedere anche

- [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)