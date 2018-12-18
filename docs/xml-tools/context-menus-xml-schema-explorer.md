---
title: Menu di scelta rapida (XML Schema Explorer) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ce9b5cc1c390d9bad108df417855a733d5dcef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus-xml-schema-explorer"></a>Menu di scelta rapida (XML Schema Explorer)
Le seguenti voci di menu di scelta rapida sono usate per eseguire ricerche specifiche dello schema nonché altre operazioni.  
  
## <a name="node-type-schema-set"></a>Tipo di nodo: set di schemi  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo del set di schemi.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Mostra elementi radice più probabili**|Consente di individuare ed evidenziare tutti gli elementi globali ai quali non fanno riferimento gli altri elementi globali.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali nel set di schemi.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali nel set di schemi.|  
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## <a name="node-type-namespace"></a>Tipo di nodo: spazio dei nomi  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo dello spazio dei nomi.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Mostra tutti i riferimenti in ingresso**|Consente di individuare ed evidenziare i file che importano lo spazio dei nomi selezionato.|  
|**Mostra tutti i riferimenti in uscita**|Per ogni file presente nello spazio dei nomi selezionato, consente di individuare ed evidenziare gli elementi seguenti:<br /><br /> -Tutti gli spazi dei nomi a cui fa riferimento istruzioni import senza un `schemaLocation` attributo.<br />-Tutti i file in spazi dei nomi diverso da quello selezionato che sono specificati nel `schemaLocation` attributo nell'importazione e includere istruzioni.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali nello spazio di nomi selezionato.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali nello spazio di nomi selezionato.|  
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## <a name="node-type-file"></a>Tipo di nodo: file  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo di file.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Mostra tutti i riferimenti in ingresso**|Consente di individuare ed evidenziare tutti i file che specificano il file selezionato negli attributi `schemaLocation` delle istruzioni Import e Include.|  
|**Mostra tutti i riferimenti in uscita**|Consente di individuare ed evidenziare gli elementi seguenti:<br /><br /> -Le istruzioni non dispone di import tutti gli spazi dei nomi specificati negli attributi dello spazio dei nomi di tutti i `schemaLocation` attributo.<br />-Tutti i file specificati nel `schemaLocation` gli attributi di tutti import e include istruzioni.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali in questo file.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali in questo file.|  
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|  
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## <a name="all-global-node-types"></a>Tutti i tipi di nodo globali  
 Nella tabella seguente vengono descritte le opzioni disponibili per tutti i nodi globali.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Mostra in visualizzazione grafico**|Consente di aprire la visualizzazione grafico. Se il nodo selezionato non si trova nell'area di lavoro, aggiungerlo all'area di lavoro e selezionarlo.|  
|**Mostra nella visualizzazione modello di contenuto**|Consente di aprire la visualizzazione modello di contenuto. Se il nodo selezionato non si trova nell'area di lavoro, aggiungerlo all'area di lavoro e selezionarlo.|  
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|  
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## <a name="node-type-element"></a>Tipo di nodo: elemento  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi dell'elemento dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Vai a definizione di tipo**|Consente di passare alla definizione di tipo dell'elemento selezionato. È applicabile quando per l'elemento viene usato un tipo globale.|  
|**Passare all'elemento originale**|Per i riferimenti agli elementi consente di passare alla definizione effettiva dell'elemento.|  
|**Mostra tutti i riferimenti**|Per gli elementi globali, consente di individuare ed evidenziare tutti i riferimenti all'elemento selezionato (elementi con `ref="selectedElement"`).|  
|**Mostra i membri del gruppo di sostituzione**|Per intestazioni di un gruppo di sostituzione, consente di inviduare ed evidenziare tutti gli elementi membri del gruppo di sostituzione di cui l'elemento selezionato è membro. Mostra i partecipanti diretti e indiretti.|  
|**Intestazioni del gruppo di sostituzione Mostra**|Per gli elementi globali membri di un gruppo di sostituzione, consente di inviduare ed evidenziare tutte le intestazioni dirette e indirette per l'elemento selezionato, come le seguenti:<br /><br /> -Intestazione un gruppo di sostituzione specificata nell'elemento selezionato.<br />-Intestazione un gruppo di sostituzione specificata nell'elemento head.|  
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|  
  
## <a name="node-type-global-types"></a>Tipo di nodo: tipi globali  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del tipo globale dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Mostra tipo di Base**|Se il tipo selezionato è derivato da un tipo globale, consente di passare al tipo di base del tipo selezionato.|  
|**Mostra tutti i riferimenti**|Consente di inviduare ed evidenziare tutti i riferimenti al tipo selezionato, inclusi gli elementi e attributi del tipo selezionato e i tipi derivati dal tipo selezionato.|  
|**Mostra tutti i tipi derivati**|Consente di individuare ed evidenziare tutti i tipi che sono direttamente o indirettamente derivati dal tipo selezionato.|  
|**Mostra tutti i predecessori**|Mostra tutti i tipi padre (di base).|  
  
## <a name="node-type-attribute"></a>Tipo di nodo: attributo  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi dell'attributo dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Vai a definizione di tipo**|Se per l'attributo è usato un tipo globale, consente di passare alla definizione di tipo dell'attributo selezionato.|  
|**Vai all'attributo originale**|Per i riferimenti agli attributi consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i riferimenti**|Per gli attributi globali, consente di individuare ed evidenziare tutti i riferimenti (altri attributi con `ref="selectedAttribute"`) all'attributo selezionato.|  
  
## <a name="node-type-attribute-group"></a>Tipo di nodo: gruppo di attributi  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del gruppo di attributi dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Vai a definizione**|Per i riferimenti consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i membri**|Consente di individuare ed evidenziare tutti i membri del gruppo di attributi.|  
|**Mostra tutti i riferimenti**|Consente di individuare ed evidenziare tutti i riferimenti (gruppi di attributi con `ref="selectedAttributeGroup"`) al gruppo di attributi selezionato.|  
  
## <a name="node-type-named-group"></a>Tipo di nodo: gruppo denominato  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del gruppo denominato dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Vai a definizione**|Per i riferimenti consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i membri**|Consente di individuare ed evidenziare tutti i membri del gruppo denominato.|  
|**Mostra tutti i riferimenti**|Consente di individuare ed evidenziare tutti i riferimenti (gruppi con `ref="selectedGroup"`) al gruppo selezionato.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)   
 [Ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md)