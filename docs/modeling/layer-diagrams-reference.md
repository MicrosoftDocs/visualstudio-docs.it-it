---
title: 'Diagrammi di dipendenza: Fare riferimento | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5185b391d0374754675999bff02438efd8de83e4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="dependency-diagrams-reference"></a>Diagrammi di dipendenza: riferimento
In Visual Studio, è possibile utilizzare un *diagramma dipendenze* per visualizzare l'architettura di alto livello, logica del sistema. Un diagramma di dipendenza consente di organizzare gli elementi fisici nel sistema in gruppi logici e astratti denominati *livelli*. Questi livelli descrivono le attività principali eseguite dagli elementi o i componenti principali del sistema. Ogni livello può anche contenere livelli annidati che descrivono attività più dettagliate.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 È possibile specificare le dipendenze desiderate o esistenti tra i livelli. Queste dipendenze, rappresentate come frecce, indicano i livelli che possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Organizzando il sistema in livelli che descrivono i ruoli e funzioni distinti, un diagramma di dipendenza consente di semplificare comprendere, riutilizzare e gestire il codice.  
  
 Utilizzare un diagramma di dipendenze per eseguire le attività seguenti:  
  
-   Comunicare l'architettura logica esistente o desiderata del sistema.  
  
-   Individuare i conflitti tra il codice esistente e l'architettura desiderata.  
  
-   Visualizzare l'impatto delle modifiche nell'architettura desiderata in caso di refactoring, aggiornamento o evoluzione del sistema.  
  
-   Rafforzare l'architettura desiderata durante lo sviluppo e la manutenzione del codice includendo la convalida con le operazioni di archiviazione e compilazione.  
  
 In questo argomento vengono descritti gli elementi che è possibile utilizzare in un diagramma di dipendenza. Per ulteriori informazioni su come creare e creare i diagrammi di dipendenza, vedere [diagrammi dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md). Per ulteriori informazioni sui modelli di livello, visitare il [sito modelli e procedure](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Lettura dei diagrammi di dipendenza  
 ![Elementi dei diagrammi dipendenza](../modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 Nella tabella seguente vengono descritti gli elementi che è possibile utilizzare in un diagramma di dipendenza.  
  
|**Forma**|**Elemento**|**Descrizione**|  
|---------------|-----------------|---------------------|  
|1|**Livello**|Gruppo logico di elementi fisici nel sistema. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via.<br /><br /> Per visualizzare gli elementi che sono collegati a un livello, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti** per aprire **Esplora livello**.<br /><br /> Per ulteriori informazioni, vedere [Esplora livello](#Explorer).<br /><br /> -   **Non è consentito dipendenze Namespace** -specifica che gli elementi associati a questo livello non possono dipendere dagli spazi dei nomi specificati.<br />-   **Non è consentito di spazi dei nomi** -specifica che gli elementi associati a questo livello non devono appartenere agli spazi dei nomi specificati.<br />-   **Spazi dei nomi necessari** -specifica che gli elementi associati a questo livello devono appartenere a uno degli spazi dei nomi specificato.|  
|2|**Dipendenza**|Indica che un livello può usare la funzionalità di un altro livello, ma non viceversa.<br /><br /> -   **Direzione** -specifica la direzione della dipendenza.|  
|3|**Dipendenza bidirezionale**|Indica che un livello può usare la funzionalità di un altro livello e viceversa.<br /><br /> -   **Direzione** -specifica la direzione della dipendenza.|  
|4|**Commentoo**|Usato per aggiungere note generali al diagramma o elementi nel diagramma.|  
|5|**Collegamento commento**|Usato per collegare commenti a elementi nel diagramma.|  
  
##  <a name="Explorer"></a>Esplora livello  
 È possibile collegare ogni livello a elementi nella soluzione, come progetti, classi, spazi dei nomi, file di progetto e altre parti del software. Il numero specificato su un livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretare il numero di elementi in un livello, ricordare quanto segue:  
  
-   Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
-   Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
 Per altre informazioni sul collegamento di livelli ed elementi, vedere:  
  
-   [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)  
  
-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Per esaminare gli elementi collegati  
  
-   Nel diagramma di dipendenza, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**.  
  
     **Esplora livello** apre e visualizza gli elementi che sono collegati ai livelli selezionati. **Esplora livello** include una colonna che mostra ogni proprietà dei collegamenti dell'elemento.  
  
    > [!NOTE]
    >  Se è possibile visualizzare tutte queste proprietà, espandere il **Esplora livello** finestra.  
  
    |**Colonna in Esplora livello**|**Descrizione**|  
    |----------------------------------|---------------------|  
    |**Categorie**|Tipo di elemento, ad esempio una classe, uno spazio dei nomi, un file di origine e così via|  
    |**Livello**|Livello collegato all'elemento|  
    |**Supporta la convalida**|Se **True**, quindi il processo di convalida dei livelli è possibile verificare che il progetto sia conforme alla dipendenze a o da questo elemento.<br /><br /> Se **False**, quindi il collegamento non fa parte nel processo di convalida dei livelli.<br /><br /> Per ulteriori informazioni, vedere [diagrammi dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificatore**|Riferimento all'elemento collegato|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
