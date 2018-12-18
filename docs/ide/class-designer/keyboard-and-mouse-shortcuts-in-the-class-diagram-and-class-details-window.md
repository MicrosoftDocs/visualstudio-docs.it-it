---
title: Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe (Progettazione classi) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5a064c19dd12c0ba2e14ce3278cf7a1b36147a5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe (Progettazione classi)
È possibile usare la tastiera oltre al mouse per eseguire operazioni di spostamento in Progettazione classi e nella finestra **Dettagli classe**.

## <a name="using-the-mouse-in-class-designer"></a>Uso del mouse in Progettazione classi  
Nei diagrammi classi sono supportate le operazioni del mouse seguenti:  
  
|Combinazione del mouse|Contesto|Descrizione|  
|-----------------------|-------------|-----------------|  
|Doppio clic|Elementi forma|Apre l'editor del codice.|  
||Connettore simbolo|Espande/comprime il simbolo.|  
||Etichetta del connettore simbolo|Richiama il comando **Mostra interfaccia**.|  
|Rotellina del mouse|Diagramma classi|Scorre verticalmente.|  
|MAIUSC + rotellina del mouse|Diagramma classi|Scorre orizzontalmente.|  
|CTRL+rotellina del mouse|Diagramma classi|Ingrandisce.|  
|CTRL + MAIUSC + clic|Diagramma classi|Ingrandisce.|  
  
## <a name="using-the-mouse-in-the-class-details-window"></a>Uso del mouse nella finestra Dettagli classe  
Usando il mouse è possibile modificare l'aspetto della finestra Dettagli classe e i dati che vengono visualizzati nei modi seguenti:  
  
-   Facendo clic in qualsiasi cella modificabile è possibile modificarne il contenuto. Tutte le modifiche apportate si riflettono in tutte le posizioni in cui i dati sono archiviati o visualizzati, anche nella finestra Proprietà e nel codice sorgente.  
  
-   Se si fa clic in una cella di una riga, nella finestra Proprietà vengono visualizzate le proprietà relative all'elemento rappresentato da tale riga.  
  
-   Per cambiare la larghezza di una colonna, trascinare il bordo sul lato destro dell'intestazione della colonna fino a ottenere la larghezza desiderata.  
  
-   Per espandere o comprimere nodi di raggruppamenti o proprietà, fare clic sui simboli freccia a sinistra della riga.  
  
-   La finestra Dettagli classe contiene diversi pulsanti che consentono di creare nuovi membri nella classe corrente e di spostarsi tra i raggruppamenti dei membri nella griglia della finestra. Per altre informazioni, vedere la sezione relativa ai pulsanti della finestra Dettagli classe  
  
## <a name="using-the-keyboard-in-class-designer"></a>Uso della tastiera in Progettazione classi  
Nei diagrammi classi sono supportate le operazioni della tastiera seguenti:  
  
|Chiave|Contesto|Descrizione|  
|---------|-------------|-----------------|  
|Tasti di direzione|All'interno delle forme dei tipi|Navigazione nel contenuto della forma in un formato struttura ad albero (è supportato il wrapping per la forma). I tasti freccia sinistra e destra espandono/comprimono l'elemento corrente se è espandibile; in caso contrario permettono di passare all'elemento padre (vedere le informazioni sulla navigazione nella visualizzazione struttura ad albero per i informazioni dettagliate sul comportamento).|  
||Forme di primo livello|Consentono di spostare forme nel diagramma.|  
|MAIUSC+tasti di direzione|All'interno delle forme dei tipi|Creazione della selezione continua costituita da elementi della forma quali membri, tipi nidificati o raggruppamenti. Questi tasti di scelta rapida non supportano il wrapping.|  
|HOME|All'interno delle forme dei tipi|Passa al titolo della forma di primo livello.|  
||Forme di primo livello|Passa alla prima forma del diagramma.|  
|FINE|All'interno delle forme dei tipi|Passa all'ultimo elemento visibile all'interno della forma.|  
||Forme di primo livello|Passa all'ultima forma del diagramma.|  
|MAIUSC+HOME|All'interno della forma del tipo|Seleziona gli elementi all'interno della forma a partire dall'elemento corrente e fino a quello in primo piano sulla stessa forma.|  
|MAIUSC+END|All'interno della forma del tipo|Uguale a MAIUSC+HOME ma dall'alto verso il basso.|  
|INVIO|Tutti i contesti|Richiama l'operazione predefinita sulla forma, che è disponibile anche tramite doppio clic. Nella maggior parte dei casi si tratta di Visualizza codice, ma per alcuni elementi la definizione è differente (simboli, intestazioni di raggruppamenti, etichette di simboli).|  
|+/-|Tutti i contesti|Se l'elemento con lo stato attivo è espandibile, questi tasti espandono/comprimono l'elemento.|  
|>|Tutti i contesti|Per gli elementi con elementi figlio, espande l'elemento se è compresso e passa al primo figlio.|  
|<|Tutti i contesti|Passa all'elemento padre.|  
|ALT+MAIUSC+L|All'interno delle forme dei tipi + sulle forme dei tipi|Passa al simbolo della forma selezionata, se presente.|  
|ALT+MAIUSC+B|All'interno delle forme dei tipi + sulle forme dei tipi|Se l'elenco di tipi di base è visualizzato sulla forma del tipo e contiene più di un elemento, comprime o espande l'elenco.|  
|DELETE|Sulle forme dei tipi e le forme Commenti|Richiama il comando **Rimuovi dal diagramma**.|  
||Su tutti gli altri elementi.|Richiama il comando **Delete from Code** (Elimina dal codice) (membri, parametri, associazioni, ereditarietà, etichette di simboli).|  
|CTRL+CANC|Tutti i contesti|Richiama il comando **Delete from Code** (Elimina dal codice) sulla selezione.|  
|TAB|Tutti i contesti|Passa all'elemento figlio successivo all'interno dello stesso elemento padre (supporta il wrapping).|  
|MAIUSC+TAB|Tutti i contesti|Passa all'elemento figlio precedente all'interno dello stesso elemento padre (supporta il wrapping).|  
|BARRA SPAZIATRICE|Tutti i contesti|Alterna la selezione sull'elemento corrente.|  
  
## <a name="using-the-keyboard-in-the-class-details-window"></a>Uso della tastiera nella finestra Dettagli classe  
  
> [!NOTE]
>  Le seguenti combinazioni di tasti sono state scelte specificamente per riprodurre l'operazione di digitazione di codice.  
  
Per spostarsi nella finestra Dettagli classe, usare i seguenti tasti:  
  
|||  
|-|-|  
|Chiave|Risultato|  
|, (virgola)|Se il cursore è posizionato in una riga di parametri, viene spostato nel campo Nome del parametro successivo. Se il cursore è posizionato nell'ultima riga di parametri di un metodo, viene spostato nel campo \<aggiungi parametro>, dove è possibile creare un nuovo parametro.<br /><br /> Se il cursore è posizionato in un altro punto della finestra Dettagli classe, viene effettivamente aggiunta una virgola nel campo corrente.|  
|; (punto e virgola)<br /><br /> oppure<br /><br /> ) (parentesi di chiusura)|Sposta il cursore nel campo Nome della riga di membri successiva nella griglia della finestra Dettagli classe.|  
|Scheda|Sposta il cursore nel campo successivo, prima da sinistra a destra e poi dall'alto verso il basso. Se il cursore viene spostato da un campo in cui è stato digitato del testo, nella finestra Dettagli classe il testo viene elaborato e memorizzato se non genera un errore.<br /><br /> Se il cursore si trova in un campo vuoto, ad esempio \<aggiungi parametro>, con il tasto TAB viene spostato nel primo campo della riga successiva.|  
|\<spazio>|Sposta il cursore nel campo successivo, prima da sinistra a destra e poi dall'alto verso il basso. Se il cursore si trova in un campo vuoto, ad esempio \<aggiungi parametro>, viene spostato nel primo campo della riga successiva. Lo \<spazio> digitato immediatamente dopo una virgola viene ignorato.<br /><br /> Se il cursore si trova nel campo Riepilogo, viene aggiunto uno spazio.<br /><br /> Se il cursore si trova nella colonna Nascondi di una determinata riga, il valore della casella di controllo Nascondi viene attivato/disattivato.|  
|CTRL+TAB|Passa a un'altra finestra del documento, ad esempio dalla finestra Dettagli classe a un file di codice aperto.|  
|ESC (Escape)|Se è stata iniziata la digitazione di testo in un campo, il tasto ESC agisce da tasto di annullamento, ripristinando il valore precedente del contenuto del campo. Se la finestra Dettagli classe ha lo stato attivo generale, ma nessuna cella specifica è attiva, il tasto ESC sposta lo stato attivo dalla finestra Dettagli classe.|  
|Freccia su e freccia giù|Questi tasti spostano il cursore da riga a riga verticalmente nella griglia della finestra Dettagli classe.|  
|Freccia sinistra|Se il cursore si trova nella colonna Nome, comprime il nodo corrente della gerarchia (se aperto).|  
|Freccia destra|Se il cursore si trova nella colonna Nome, espande il nodo corrente della gerarchia (se compresso).|  
  
## <a name="see-also"></a>Vedere anche
[Creazione e configurazione di membri di tipi](creating-and-configuring-type-members.md)