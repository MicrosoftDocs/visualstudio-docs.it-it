---
title: Compressione ed espansione di aree di codice in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 64fd40d78b31c4791c699c2602528b33a36f4245
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="outlining"></a>struttura

È possibile scegliere di nascondere parti di codice comprimendo un'area di codice in modo che venga visualizzata sotto un segno più (+). Per espandere un'area compressa fare clic sul segno più. Se si preferisce usare la tastiera, per espandere e comprimere è possibile scegliere **CTRL** + **M** + **M**. È anche possibile comprimere un'area della struttura facendo doppio clic su qualsiasi riga nell'area a margine della struttura, che viene visualizzata a sinistra del codice. Il contenuto di un'area compressa può essere visualizzato come descrizione comando quando si passa il mouse sull'area compressa.

Le aree nel margine della struttura vengono evidenziate anche quando si passa il mouse sul margine. Il valore predefinito del colore dell'evidenziazione può sembrare piuttosto debole in alcune configurazioni di colore. È possibile modificarlo in **Strumenti**, **Opzioni**, **Ambiente**, **Tipi di carattere e colori**, **Area comprimibile**.

Quando si usa il codice di struttura, è possibile espandere le sezioni che si intende usare, comprimerle al termine delle operazioni e quindi passare ad altre sezioni. Quando non si vuole avere la struttura visualizzata, con il comando **Rimuovi struttura** è possibile rimuovere le informazioni sulla struttura senza alterare il codice sottostante.

I comandi **Annulla** e **Ripristina** nel menu **Modifica** hanno effetto su queste azioni. Le operazioni **Copia**, **Taglia**, **Incolla** e di trascinamento della selezione mantengono le informazioni relative alla struttura ma non lo stato dell'area comprimibile. Ad esempio, quando si copia un'area compressa, l'operazione **Incolla** incollerà il testo copiato come area espansa.

> [!CAUTION]
> Quando si modifica un'area della struttura, la struttura potrebbe andare persa. Ad esempio, le operazioni di eliminazione o Trova e Sostituisci potrebbero cancellare la parte finale dell'area.

I comandi seguenti sono disponibili nel sottomenu **Modifica****Struttura**.

|||
|-|-|
|Nascondi selezione|(CTRL + M, CTRL + H) - Consente di comprimere un blocco di codice che normalmente non sarebbe disponibile per la struttura, ad esempio un blocco `if`. Per rimuovere l'area personalizzata, usare **Visualizza selezione nascosta** (o CTRL + M, CTRL + U). Non disponibile in Visual Basic.|  
|Espandi/comprimi struttura|- Consente di invertire lo stato nascosto o espanso corrente della sezione di struttura più interna quando il cursore si trova in una sezione compressa nidificata.|  
|Attiva/disattiva tutta la struttura|(CTRL + M, CTRL + L) - Imposta tutte le aree allo stesso stato compresso o espanso. Se alcune aree sono espanse e altre compresse, quelle compresse vengono espanse.|  
|Arresta struttura|(CTRL + M, CTRL + P) - Rimuove tutte le informazioni relative alla struttura per l'intero documento.|  
|Visualizza selezione nascosta|(CTRL + M, CTRL + U) - Rimuove le informazioni relative alla struttura per l'area definita dall'utente attualmente selezionata. Non disponibile in Visual Basic.|  
|Comprimi alle definizioni|(CTRL + M, CTRL + O) - Consente di comprimere i membri di tutti i tipi.|  
|Comprimi blocco:\<limite logico>|(Visual C++) Consente di comprimere un'area nella funzione contenente il punto di inserimento. Ad esempio, se il punto di inserimento si trova all'interno di un ciclo, il ciclo è nascosto.|  
|Comprimi tutto in:\<strutture logiche>|(Visual C++) Comprime tutte le strutture all'interno della funzione.|  

È anche possibile usare Visual Studio SDK per definire le aree di testo che si intende espandere o comprimere. Vedere [Walkthrough: Outlining](../extensibility/walkthrough-outlining.md) (Procedura dettagliata: struttura).

## <a name="see-also"></a>Vedere anche

[Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)