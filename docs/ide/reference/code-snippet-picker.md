---
title: Selezione frammento di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 47eb9c801f638f108a8096b456784278e019f56d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="code-snippet-picker"></a>Selezione frammento di codice

L'editor del codice di Visual Studio include la **Selezione frammento di codice** che consente, in pochi clic del mouse, di inserire blocchi di codice pronti nel documento attivo.

La procedura per visualizzare la **Selezione frammento di codice** varia in base al linguaggio in uso.

- Visual Basic- Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento**.

- C# - Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento** o **Racchiudi tra**.

- C++ - La **Selezione frammento di codice** non è disponibile.

- F# - La **Selezione frammento di codice** non è disponibile.

- JavaScript - Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento** o **Racchiudi tra**.

- XML - Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento** o **Racchiudi tra**.

- HTML - Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento** o **Racchiudi tra**.

- SQL - Fare clic con il pulsante destro del mouse nella posizione desiderata nell'editor del codice per visualizzare il menu di scelta rapida e quindi scegliere **Inserisci frammento**.

Nella maggior parte dei linguaggi di sviluppo di Visual Studio, è possibile usare **Gestione frammenti di codice** per aggiungere cartelle all'elenco cartelle in cui la **Selezione frammento di codice** cerca i file di frammenti di codice XML. È anche possibile creare frammenti personalizzati da aggiungere all'elenco. Per altre informazioni, vedere [Procedura dettagliata: creazione di un frammento di codice](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Elenco UIElement

Nome elemento  
Campo di testo modificabile che visualizza il nome dell'elemento selezionato in **Elenco elementi**. Per eseguire una ricerca incrementale per l'elemento desiderato, iniziare a digitarne il nome in questo campo. Continuare aggiungendo lettere fino a quando l'elemento desiderato non viene selezionato nell'**Elenco elementi**.

Elenco elementi  
Elenco di frammenti di codice disponibili per l'inserimento o un elenco di cartelle che contengono frammenti di codice. Per inserire un frammento di codice o espandere una cartella, selezionare l'elemento desiderato e premere INVIO.

## <a name="see-also"></a>Vedere anche

[Procedure consigliate per l'uso dei frammenti di codice](../../ide/best-practices-for-using-code-snippets.md)  
[Frammenti di codice IntelliSense di Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  
[Impostazione di segnalibri nel codice](../../ide/setting-bookmarks-in-code.md)  
[Procedura: Usare frammenti di codice racchiusi](../../ide/how-to-use-surround-with-code-snippets.md)