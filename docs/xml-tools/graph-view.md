---
title: Visualizzazione del grafico di Progettazione XML Schema
description: Informazioni sulla visualizzazione grafico in Progettazione XML Schema che fornisce una rappresentazione grafica dei nodi dello schema globale e delle relazioni tra i nodi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 39a988ed4742f34fa2a3e6e2680d5eec8ccd2b07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879306"
---
# <a name="graph-view"></a>Visualizzazione grafico

Visualizzazione grafico fornisce una rappresentazione grafica dei nodi dello schema globali e delle relazioni tra i nodi. Si noti che la visualizzazione grafico non consente di modificare il layout del set di schemi nell'area di progettazione. Visualizzazione grafico include anche la barra degli strumenti Progettazione XML Schema e la barra di navigazione.

Nell'immagine seguente viene illustrata la visualizzazione grafico con sei nodi globali sulla relativa area di progettazione.

![Visualizzazione del grafico di Progettazione XML Schema](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Area di progettazione

Nell'area di progettazione della visualizzazione grafico viene visualizzato il contenuto dell' [area di lavoro XML Schema Designer](../xml-tools/xml-schema-designer-workspace.md). Se l'area di lavoro contiene eventuali nodi globali del set di schemi, i nodi vengono mostrati nell'area di progettazione della visualizzazione grafico e vengono tracciate frecce tra i nodi tra cui intercorrono relazioni.

Facendo doppio clic su un nodo nella visualizzazione grafico, viene visualizzato l'editor XML.

Per eliminare i nodi selezionati dall'area di lavoro, utilizzare la barra degli strumenti di progettazione XSD o il tasto **Canc** .

Se l'area di progettazione è vuota, vengono visualizzati l'editor XML, **XML Schema Explorer** e la filigrana. La *filigrana* è un elenco di collegamenti a tutte le visualizzazioni di progettazione XSD.

![Progettazione XSD; Visualizzazione del grafico](../xml-tools/media/xsdgraphviewwatermark.gif)

Se il set di schemi contiene errori, alla fine dell'elenco viene visualizzato il testo: "Usare l'elenco degli errori per visualizzare e correggere gli errori nel set di schemi".

## <a name="breadcrumb-bar"></a>Barra di navigazione

Tramite la barra di navigazione nella parte inferiore della visualizzazione grafico viene mostrato dove si trova il nodo selezionato nel set di schemi. Se vengono selezionati più elementi, la barra di navigazione sarà vuota.

## <a name="context-right-click-menu"></a>Menu di scelta rapida (con pulsante destro del mouse)

Nella tabella seguente vengono descritte le opzioni disponibili per tutti i nodi nell'area di progettazione della visualizzazione grafico.

|Opzione|Descrizione|
|-|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico (visualizzato in grigio).|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Esporta diagramma come immagine**|Salva l'area di progettazione in un file XPS.|
|**Seleziona tutto**|Seleziona tutti i nodi nell'area di progettazione.|
|**Visualizza codice**|Apre il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato in **XML Schema Explorer** è selezionato anche nell'editor XML.|
|**Finestra Proprietà**|Apre la finestra **Proprietà** , se non è già aperta. In questa finestra verranno visualizzate le informazioni sul nodo.|

Oltre alle opzioni comuni descritte in precedenza, nel menu di scelta rapida per gli elementi globali sono disponibili anche le opzioni seguenti:

|Opzione|Descrizione|
|-|-----------------|
|**Aggiungi definizione di tipo**|Aggiunge il tipo base al diagramma.|
|**Aggiungi tutti i riferimenti**|Aggiunge tutti i nodi che fanno riferimento all'elemento e disegna frecce che indicano le relazioni tra loro.|
|**Aggiungi membri del gruppo di sostituzione**|Aggiunge tutti i membri del gruppo di sostituzione. Questa opzione viene visualizzata se l'elemento è l'intestazione o il membro di un gruppo di sostituzione.|
|**Genera XML di esempio**|Consente di generare un file XML di esempio per l'elemento globale.|

Oltre alle opzioni comuni descritte in precedenza, nel menu di scelta rapida per i tipi semplici e complessi globali sono disponibili anche le opzioni seguenti:

|Opzione|Descrizione|
|-|-----------------|
|**Aggiungi tipo di base**|Se il tipo selezionato è derivato da un tipo globale, aggiunge il tipo di base del tipo selezionato.|
|**Aggiungi tutti i riferimenti**|Aggiunge tutti i riferimenti del tipo selezionato, inclusi gli elementi e attributi del tipo selezionato e i tipi derivati dal tipo selezionato.|
|**Aggiungi tutti i tipi derivati**|Aggiunge tutti i tipi direttamente e indirettamente derivati dal tipo selezionato.|
|**Aggiungi tutti i predecessori**|Aggiunge tutti i tipi padre (di base).|

Oltre alle opzioni comuni descritte in precedenza, nel menu di scelta rapida per i gruppi di attributi e globali sono disponibili anche le opzioni seguenti:

|Opzione|Descrizione|
|-|-----------------|
|**Aggiungi tutti i riferimenti**|Aggiunge tutti i nodi che fanno riferimento al gruppo e disegna frecce che indicano le relazioni tra loro.|
|**Aggiungi tutti i membri**|Aggiunge tutti i membri del gruppo e disegna frecce che indicano le relazioni tra loro.|

Oltre alle opzioni comuni descritte in precedenza, nel menu di scelta rapida per gli attributi globali sono disponibili anche le opzioni seguenti:

|Opzione|Descrizione|
|-|-----------------|
|**Aggiungi tutti i riferimenti**|Aggiunge tutti i nodi che fanno riferimento al gruppo e disegna frecce che indicano le relazioni tra loro.|

## <a name="properties-window"></a>Finestra Proprietà

Utilizzare il menu di scelta rapida (clic con il pulsante destro del mouse) per aprire inizialmente la finestra **Proprietà** . Per impostazione predefinita, la finestra **Proprietà** viene visualizzata nell'angolo inferiore destro di Visual Studio. Quando si fa clic su un nodo di cui viene eseguito il rendering nella visualizzazione modello di contenuto, le proprietà di tale nodo verranno visualizzate nella finestra **Proprietà** .

## <a name="xsd-toolbar"></a>Barra degli strumenti XSD

I seguenti pulsanti della barra degli strumenti XSD sono abilitati quando la visualizzazione grafico è attiva.

![Barra degli strumenti di Progettazione XML Schema](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Opzione|Descrizione|
|-|-----------------|
|**Mostra visualizzazione iniziale**|Passa alla [visualizzazione iniziale](../xml-tools/start-view.md). È possibile accedere a questa visualizzazione tramite il tasto di scelta rapida: **CTRL** + **1**.|
|**Mostra visualizzazione modello di contenuto**|Passa alla [visualizzazione modello di contenuto](../xml-tools/content-model-view.md). È possibile accedere a questa visualizzazione tramite il tasto di scelta rapida: **CTRL** + **2**.|
|**Mostra visualizzazione grafico**|Passa alla [visualizzazione grafico](../xml-tools/graph-view.md). È possibile accedere a questa visualizzazione tramite il tasto di scelta rapida: **CTRL** + **3**.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione. Questa opzione è abilitata nella visualizzazione modello di contenuto e nella visualizzazione grafico.|
|**Da sinistra a destra**|Modifica il layout nella visualizzazione grafico in una rappresentazione gerarchica da sinistra a destra dei nodi. È possibile accedere a questa opzione tramite la scelta rapida da tastiera: **ALT** + **freccia destra**.|
|**Da destra a sinistra**|Modifica il layout nella visualizzazione grafico in una rappresentazione gerarchica da destra a sinistra dei nodi. È possibile accedere a questa opzione tramite il tasto di scelta rapida: **ALT** + **freccia sinistra**.|
|**Dall'alto in basso**|Modifica il layout nella visualizzazione grafico in una rappresentazione gerarchica dall'alto in basso dei nodi. È possibile accedere a questa opzione tramite la scelta rapida da tastiera: **ALT** + **freccia giù**.|
|**Dal basso verso l'alto**|Modifica il layout nella visualizzazione grafico in una rappresentazione gerarchica dal basso in alto dei nodi. È possibile accedere a questa opzione tramite il tasto di scelta rapida: **ALT** + **freccia su**.|

## <a name="panscroll"></a>Panoramica/scorrimento

È possibile creare una panoramica dell'area di progettazione usando le barre di scorrimento oppure tenendo premuto il tasto **CTRL** mentre si fa clic e si trascina il mouse. Quando si esegue una panoramica dell'area di progettazione tramite selezione e trascinamento, il cursore sarà modificato in quattro frecce incrociate che puntano in quattro direzioni.

## <a name="undoredo"></a>Annullamento/ripristino

La funzionalità di annullamento/ripristino è abilitata nella visualizzazione grafico per le seguenti azioni:

- Aggiunta di un singolo nodo con trascinamento della selezione.

- Aggiunta di più nodi dalla finestra dei risultati della ricerca nelle query relative a Schema Explorer o alla visualizzazione iniziale.

- Eliminazione di uno o più nodi.

## <a name="zoom"></a>Zoom

Lo zoom è disponibile nell'angolo inferiore destro della visualizzazione grafico.

È possibile controllare lo zoom nei seguenti modi:

- Tenendo premuto il tasto **CTRL** e ruotando la rotellina del mouse quando si posiziona il mouse sull'area di visualizzazione del grafico.

- Tramite il dispositivo di scorrimento. Il dispositivo di scorrimento mostra il livello di zoom corrente.

Il dispositivo di scorrimento zoom è opaco quando lo si seleziona, si posiziona il puntatore del mouse su di esso oppure si usa **CTRL** con la rotellina del mouse per ingrandire in tutti gli altri momenti, è trasparente.

## <a name="xml-editor-integration"></a>Integrazione dell'editor XML

È possibile spostarsi avanti e indietro tra la visualizzazione grafico e l'editor XML facendo clic su un nodo e usando il menu Visualizza contesto codice (clic con il pulsante destro del mouse).

Se si apportano modifiche al set di schemi nell'editor XML, le modifiche verranno sincronizzate nella visualizzazione grafico. Per ulteriori informazioni, vedere [integrazione con l'editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vedi anche

- [Area di progettazione](../xml-tools/xml-schema-designer-workspace.md)
