---
title: Cerca nei file | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0e87022cb3159e48a92e35ee07987bef6ce68f9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="find-in-files"></a>Cerca nei file

**Cerca nei file** consente di eseguire ricerche in un set di file specificato. Le corrispondenze trovate e le azioni eseguite sono elencate nella finestra **Risultati ricerca** selezionata in **Opzioni risultati**.

Per visualizzare **Cerca nei file** nella finestra **Trova e sostituisci** è possibile usare uno dei metodi seguenti.

## <a name="to-display-find-in-files"></a>Per visualizzare Cerca nei file

1. Nella barra dei menu scegliere **Modifica**, **Trova e sostituisci**.

1. Scegliere **Cerca nei file**.

Per annullare un'operazione di ricerca, premere **Ctrl** + **Interr**.

> [!NOTE]
> Lo strumento Trova e sostituisci non esegue la ricerca nelle directory con l'attributo `Hidden` o `System`.

## <a name="find-what"></a>Trova

Per cercare una nuova stringa di testo o espressione, specificarla nella casella. Per cercare una delle 20 stringhe cercate più di recente, aprire l'elenco a discesa e scegliere una stringa. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di ricerca. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Il pulsante **Generatore di espressioni** viene abilitato solo se è stata selezionata l'opzione **Usa espressioni regolari** in **Opzioni di ricerca**.

## <a name="look-in"></a>Cerca in

L'opzione selezionata nell'elenco a discesa **Cerca in** determina se la funzionalità **Cerca nei file** deve cercare solo nei file attualmente attivi o in tutti i file archiviati all'interno di determinate cartelle. Selezionare un ambito di ricerca nell'elenco o fare clic sul pulsante **Sfoglia (...)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di directory desiderato. È anche possibile digitare un percorso direttamente nella casella **Cerca in**.

> [!WARNING]
> Con le opzioni **Intera soluzione** o **Progetto corrente**, la ricerca non viene eseguita nei file di progetto e di soluzione. Se si vuole cercare in file di progetto, scegliere una cartella di ricerca.

> [!NOTE]
> Se l'opzione **Cerca in** selezionata fa sì che venga cercato un file estratto dal controllo del codice sorgente, la ricerca verrà eseguita solo nella versione del file scaricata nel computer locale.

## <a name="include-subfolders"></a>Includi sottocartelle

Specifica che la ricerca verrà eseguita nelle sottocartelle della cartella **Cerca in**.

## <a name="find-options"></a>Opzioni ricerca

È possibile espandere o comprimere la sezione **Opzioni di ricerca**. È possibile selezionare o deselezionare le opzioni seguenti:

Maiuscole/minuscole  
Se questa opzione è selezionata, in una ricerca impostata su **Risultati ricerca** viene applicata la distinzione tra maiuscole e minuscole

Parola intera  
Se questa opzione è selezionata, la finestra **Risultati ricerca** restituirà solo corrispondenze di parole intere.

Utilizza espressioni regolari  
Se questa casella di controllo è selezionata, è possibile usare notazioni speciali per definire modelli di testo che devono corrispondere nelle caselle di testo **Trova** o **Sostituisci con**. Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Cerca i seguenti tipi di file  
L'elenco indica i tipi di file da cercare nelle directory **Cerca in**. Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file contenuti nelle directory **Cerca in**.

Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.

## <a name="result-options"></a>Opzioni risultati

È possibile espandere o comprimere la sezione **Opzioni risultati**. È possibile selezionare o deselezionare le opzioni seguenti:

Finestra Risultati ricerca 1  
Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1**. Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 1**.

Finestra Risultati ricerca 2  
Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**. Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.

Mostra solo nomi file  
Mostra un elenco di file che contengono le corrispondenze invece di visualizzare le corrispondenze stesse.

Accoda risultati  
Aggiunge i risultati della ricerca a quelli della ricerca precedente.

## <a name="see-also"></a>Vedere anche

[Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)  
[Sostituisci nei file](../ide/replace-in-files.md)  
[Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)