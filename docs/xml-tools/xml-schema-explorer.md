---
title: XML Schema Explorer | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84aead3cf496a28e67e6440fb77b8cbf4aca6462
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer
XML Schema Explorer è integrato con Microsoft Visual Studio e con l'editor XML per consentire di usare gli schemi XML Schema Definition Language (XSD). Quando si apre un file di XML Schema, il **Set di schemi** nodo viene visualizzato in XML Schema Explorer. In XML Schema Explorer vengono visualizzati anche tutti gli schemi inclusi, importati o ridefiniti per il file di destinazione e qualsiasi file a cui viene fatto riferimento tramite un'istruzione `include` o `import`.  
  
 XML Schema Explorer consente di eseguire le operazioni seguenti:  
  
-   Ottenere una rapida panoramica del set di schemi.  
  
-   Esplorare e spostarsi all'interno dell'albero.  
  
-   Eseguire ricerche per parola chiave e specifiche dello schema. Per ulteriori informazioni, vedere [la ricerca del Set di schemi](../xml-tools/searching-the-schema-set.md).  
  
-   Aggiungere i risultati della ricerca alla visualizzazione grafico o alla visualizzazione modello di contenuto  
  
-   Ordinare l'albero in base a nome, tipo o ordine dei documenti. Per ulteriori informazioni, vedere [ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
-   Aprire l'editor XML e passare ai percorsi del codice nel file XSD. Per ulteriori informazioni, vedere [integrazione con l'Editor XML](../xml-tools/integration-with-xml-editor.md).  
  
-   Generare codice XML di esempio per gli elementi globali.  
  
XML Schema Explorer fornisce una visualizzazione gerarchica del set di schemi tramite una visualizzazione ad albero. XML Schema Explorer offre inoltre funzionalità di ricerca, filtro, navigazione e ordinamento. Per accedere a XML Schema Explorer, eseguire una delle operazioni seguenti:  
  
-   Se si utilizza il [visualizzazione iniziale](../xml-tools/start-view.md), fare clic su di **XML Schema Explorer** collegamento.  
  
-   Se si utilizza il [visualizzazione grafico](../xml-tools/graph-view.md) o [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) e dispone di nodi nell'area di lavoro, utilizzare il menu di scelta rapida per selezionare XML Schema Explorer.  
  
-   È inoltre possibile selezionare il Explorerfrom di XML Schema di **vista** menu.  
  
-   È possibile accedere il Explorerfrom di Schema XML un file con estensione vb con un valore letterale della XML Visual Basic associata a un file XSD. Per visualizzare lo schema di set di XML Schema Explorer, fare clic destro del mouse su un nodo XML in un valore letterale XML o un'importazione dello spazio dei nomi XML e selezionare il **Mostra in Schema Explorer** comando. Per ulteriori informazioni, vedere [integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Visualizzazione albero  
 In XML Schema Explorer le informazioni sul set di schemi precompilati vengono visualizzate in una struttura ad albero. La struttura ad albero è organizzata come segue:  
  
-   Al livello principale è presente il nodo del set di schemi.  
  
-   Il secondo livello contiene gli spazi dei nomi.  
  
-   Nel terzo livello sono presenti i file.  
  
-   Il quarto livello contiene i nodi globali e può includere elementi, gruppi, tipi complessi, tipi semplici, attributi, gruppi di attributi e istruzioni `include`, `import` e `redefine`.  
  
Di seguito viene riportato un esempio di struttura ad albero:  
  
![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Selezione e attivazione  
 Per evidenziare e selezionare un nodo, fare clic una volta in Schema Explorer.  
  
 Per attivare un nodo, fare doppio clic oppure premere **invio** quando si seleziona il nodo.  
  
-   L'attivazione di un nodo consente di aprire il file in cui questo nodo è definito (se non è già aperto) e di selezionare il nodo nel file.  
  
-   L'attivazione di un nodo di file consente di aprire il file selezionato (se non è già aperto) e di evidenziare il nodo `<schema>`.  
  
-   L'attivazione di un nodo set di schemi o spazio dei nomi non esegue alcuna operazione.  
  
## <a name="draging-and-dropping-nodes"></a>Trascinamento di nodi  
 È possibile trascinare e rilasciare nodi globali, nodi di file e nodi spazio dei nomi su una visualizzazione di Progettazione XSD. Se la visualizzazione corrente è il [visualizzazione iniziale](../xml-tools/start-view.md), trascinare un nodo sulla visualizzazione verrà aperto il [visualizzazione grafico](../xml-tools/graph-view.md). Se la visualizzazione corrente è il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) o visualizzazione grafico, la visualizzazione non cambierà quando si elimina un nodo su di esso.  
  
 Eliminazione di file sulla visualizzazione aggiungerà tutti i nodi globali contenuti nel file di [area di progettazione XSD](../xml-tools/xml-schema-designer-workspace.md). Il rilascio degli spazi dei nomi sulla visualizzazione aggiungerà tutti i nodi globali contenuti nello spazio dei nomi all'area di lavoro. L'area di lavoro è condivisa da tutte le visualizzazioni.  
  
 Non è possibile trascinare nodi locali o importazioni.  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md)  
  
-   [L'ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)