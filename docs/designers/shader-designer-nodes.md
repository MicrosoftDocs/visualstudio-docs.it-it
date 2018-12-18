---
title: Nodi della finestra di progettazione shader
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7d4bb2633571a552c13bda0795d05447f9e340c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="shader-designer-nodes"></a>Nodi della finestra di progettazione shader
Gli articoli di questa sezione della documentazione contengono informazioni sui diversi nodi di progettazione shader che possono essere usati per creare vari effetti grafici.

## <a name="nodes-and-node-types"></a>Nodi e tipi di nodo
 La finestra di progettazione shader rappresenta gli effetti visivi sotto forma di grafo. Questi grafi sono costituiti da nodi scelti specificamente e connessi in modo preciso per ottenere l'effetto voluto. Ogni nodo rappresenta un'informazione o una funzione matematica, mentre le connessioni tra di essi rappresentano il modo in cui le informazioni attraversano il grafico per produrre il risultato. La finestra di progettazione shader offre sei diversi tipi di nodi (filtri, nodi di trama, parametri, costanti, nodi di utilità e nodi di matematica) e ogni tipo di nodo include numerosi nodi singoli. Negli altri articoli in questa sezione vengono descritti questi nodi e tipi di nodi. Vedere i collegamenti alla fine di questo documento.

## <a name="node-structure"></a>Struttura del nodo
 Tutti i nodi sono costituiti da una combinazione di elementi comuni. Ogni nodo possiede almeno un terminale di output sul lato destro (ad eccezione del nodo di colore finale, che rappresenta l'output dello shader). I nodi che rappresentano calcoli o campionatori di trame possiedono terminali di input sul lato sinistro ma i nodi che rappresentano informazioni non hanno terminali di input. I terminali di output sono connessi ai terminali di input per trasmettere le informazioni da un nodo a un altro.

### <a name="promotion-of-inputs"></a>Promozione degli input
 Poiché la finestra di progettazione shader deve alla fine generare codice sorgente HLSL in modo da poter usare l'effetto in un gioco o in un'app, i nodi di progettazione shader sono soggetti alle regole di promozione tipo usate da HLSL. Poiché l'hardware grafico opera principalmente su valori a virgola mobile, la promozione tipo tra tipi diversi, ad esempio da `int` a `float` o da `float` a `double`, non è comune. In alternativa, poiché l'hardware grafico usa la stessa operazione su più informazioni contemporaneamente, può verificarsi un tipo diverso di promozione in cui il più breve di un determinato numero di input viene allungato fino a corrispondere alla dimensione dell'input più lungo. Le modalità dell'allungamento dipendono dal tipo di input e anche dall'operazione in sé:

-   **Se il tipo più piccolo è un valore scalare:**

     Il valore dello scalare viene replicato in un vettore di dimensioni pari all'input più grande. Ad esempio, l'input scalare 5.0 diventa il vettore (5.0, 5.0, 5.0) quando l'input maggiore dell'operazione è un vettore di tre elementi, indipendentemente dall'operazione.

-   **Se il tipo più piccolo è un vettore e l'operazione è di tipo moltiplicativo (\*, /, % e così via):**

     Il valore del vettore viene copiato negli elementi iniziali di un vettore di dimensioni pari all'input di dimensioni maggiori e gli elementi finali vengono impostati su 1.0. Ad esempio, l'input di vettore (5.0, 5.0) diventa il vettore (5.0, 5.0, 1.0, 1.0) quando viene moltiplicato per un vettore con quattro elementi. Ciò consente di mantenere il terzo e il quarto elemento dell'output usando l'identità moltiplicativa, 1.0.

-   **Se il tipo più piccolo è un vettore e l'operazione è di tipo additivo (+,-, e così via):**

     Il valore del vettore viene copiato negli elementi iniziali di un vettore di dimensioni pari all'input di dimensioni maggiori e gli elementi finali vengono impostati su 0.0. Ad esempio, l'input di vettore (5.0, 5.0) diventa il vettore (5.0, 5.0, 0.0, 0.0) quando viene aggiunto a un vettore con quattro elementi. Ciò consente di mantenere il terzo e il quarto elemento dell'output usando l'identità additiva, 0.0.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Nodi costanti](../designers/constant-nodes.md)|Vengono descritti i nodi che è possibile usare per rappresentare i valori letterali e le informazioni di stato vertex interpolate nei calcoli dello shader. Poiché lo stato vertex è interpolato e quindi diverso per ogni pixel, a ogni istanza di pixel shader viene assegnata una versione diversa della costante.|
|[Nodi Parameter](../designers/parameter-nodes.md)|Descrive i nodi che è possibile usare per rappresentare posizione della fotocamera, proprietà del materiale, parametri di illuminazione, ora e altre informazioni sullo stato dell'app nei calcoli dello shader.|
|[Nodi di trama](../designers/texture-nodes.md)|Descrive i nodi che è possibile usare per effettuare il campionamento di più geometrie e tipi di trama e i modi comuni per produrre o trasformare le coordinate di trama.|
|[Nodi di matematica](../designers/math-nodes.md)|Descrive i nodi che è possibile usare per eseguire operazioni algebriche, logiche, trigonometriche e altre operazioni matematiche che eseguono il mapping direttamente alle istruzioni di HLSL.|
|[Nodi utilità](../designers/utility-nodes.md)|Descrive i nodi che è possibile usare per eseguire calcoli di illuminazione comuni e altre operazioni comuni che non eseguono il mapping direttamente alle istruzioni di HLSL.|
|[Nodi del filtro](../designers/filter-nodes.md)|Descrivei i nodi che è possibile usare per eseguire il filtraggio della trama e del colore.|