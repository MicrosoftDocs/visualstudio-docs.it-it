---
title: Visualizzazione della gerarchia di chiamata in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d18af9f159c663cb061a32a61343eaa0a14d7503
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="view-call-hierarchy"></a>Visualizzare la gerarchia di chiamata

Visualizzando la gerarchia di chiamata per il codice è possibile esplorare tutte le chiamate da e verso un metodo, una proprietà o un costruttore selezionato. Ciò consente di comprendere meglio il flusso del codice e di valutare gli effetti delle modifiche al codice. È possibile esaminare diversi livelli del codice per visualizzare le complesse catene di chiamate di metodi e i punti di ingresso aggiuntivi al codice. In questo modo è possibile esplorare tutti i possibili percorsi di esecuzione.

In Visual Studio, è possibile visualizzare una gerarchia di chiamata in fase di progettazione. Ciò significa che non è necessario impostare un punto di interruzione e avviare il debugger per visualizzare lo stack di chiamate della fase di esecuzione.

## <a name="use-the-call-hierarchy-window"></a>Usare la finestra Gerarchia di chiamata

Per visualizzare la finestra **Gerarchia di chiamata**, fare clic con il pulsante destro del mouse sul nome di una chiamata a un metodo, una proprietà o un costruttore e quindi scegliere **Visualizza gerarchia delle chiamate**.

Il nome del membro viene visualizzato in un riquadro con visualizzazione struttura ad albero nella finestra **Gerarchia di chiamata**. Se si espande il nodo del membro, vengono visualizzati i sottonodi **Chiamate a** *nome membro* e **Chiamate da** *nome membro*. La figura seguente mostra questi nodi nella finestra **Gerarchia di chiamata**.

![Gerarchia di chiamata con un nodo aperto](../../ide/reference/media/onenode.png "OneNode")

- Se si espande il nodo **Chiamate a**, vengono visualizzati tutti i membri che chiamano il membro selezionato.

- Se si espande il nodo **Chiamate da**, vengono visualizzati tutti i membri chiamati dal membro selezionato.

È quindi possibile espandere ognuno di questi membri dei sottonodi nei nodi **Chiamate a** e **Chiamate da**. In questo modo è possibile spostarsi nello stack dei chiamanti, come illustrato nella figura seguente.

![Gerarchia di chiamata con più nodi aperti](../../ide/media/multiplenodes.png "MultipleNodes")

Per i membri definiti come virtuali o astratti viene visualizzato un nodo **Overrides method name** (Esegui override nome metodo). Per i membri di interfaccia viene visualizzato un nodo **Implements method name** (Implementa nome metodo). Questi nodi espandibili vengono visualizzati allo stesso livello dei nodi **Chiamate a** e **Chiamate da**.

La casella **Ambito di ricerca** sulla barra degli strumenti include le opzioni **Soluzione personale**, **Progetto corrente** e **documento corrente**.

Quando si seleziona un membro figlio nel riquadro della visualizzazione struttura ad albero **Gerarchia di chiamata**:

- Il riquadro dei dettagli **Gerarchia di chiamata** visualizza tutte le righe di codice in cui tale membro figlio viene chiamato dal membro padre.

- La **finestra Definizione codice**, se aperta, visualizza il codice per il membro selezionato (solo C++). Per altre informazioni su questa finestra, vedere [Visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> La funzionalità Gerarchia di chiamata non trova riferimenti ai gruppi di metodi, che includono le posizioni in cui un metodo viene aggiunto come gestore eventi o assegnato a un delegato. Per trovare tutti i riferimenti a un metodo, è possibile usare il comando **Trova tutti i riferimenti**.

### <a name="shortcut-menu-items"></a>Comandi del menu di scelta rapida

La tabella seguente descrive i vari comandi del menu di scelta rapida disponibili quando si fa clic con il pulsante destro del mouse su un nodo nel riquadro della visualizzazione struttura ad albero.

|Comando del menu di scelta rapida|Descrizione|
|-----------------------|-----------------|
|**Aggiungi come nuova radice**|Aggiunge il nodo selezionato al riquadro della visualizzazione struttura ad albero come un nuovo nodo radice. Questo permette di concentrare l'attenzione su un sottoalbero specifico.|
|**Rimuovi radice**|Rimuove il nodo radice selezionato dal riquadro di visualizzazione albero. Questa opzione è disponibile solo da un nodo radice.<br /><br /> È anche possibile usare il pulsante della barra degli strumenti **Rimuovi radice** per rimuovere il nodo radice selezionato.|
|**Vai a definizione**|Esegue il comando Vai a definizione nel nodo selezionato. Questo comando consente di passare alla definizione originale per una chiamata al membro o una definizione di variabile.<br /><br /> Per eseguire il comando Vai a definizione, è anche possibile fare doppio clic sul nodo selezionato o premere F12 nel nodo selezionato.|
|**Trova tutti i riferimenti**|Esegue il comando Trova tutti i riferimenti nel nodo selezionato. Questo comando consente di trovare tutte le righe di codice nel progetto che fanno riferimento a una classe o a un membro.<br /><br /> È anche possibile usare MAIUSC + F12 per eseguire il comando Trova tutti i riferimenti nel nodo selezionato.|
|**Copia**|Copia il contenuto del nodo selezionato (ma non i sottonodi).|
|**Aggiorna**|Comprime il nodo selezionato in modo che espandendolo nuovamente vengano visualizzate le informazioni più recenti.|