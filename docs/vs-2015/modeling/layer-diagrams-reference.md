---
title: 'I diagrammi livello: Riferimento | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 904b92a058b8fb50f3f2e53f093f4add3730dfbf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783220"
---
# <a name="layer-diagrams-reference"></a>Diagrammi livello: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile usare una *diagramma livello* per visualizzare l'architettura di alto livello, logica del sistema. Un diagramma livello organizza gli elementi fisici nel sistema in gruppi logici astratti, chiamati *livelli*. Questi livelli descrivono le attività principali eseguite dagli elementi o i componenti principali del sistema. Ogni livello può anche contenere livelli annidati che descrivono attività più dettagliate.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 È possibile specificare le dipendenze desiderate o esistenti tra i livelli. Queste dipendenze, rappresentate come frecce, indicano i livelli che possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Organizzando il sistema in livelli che descrivono funzioni e ruoli distinti, un diagramma livello può semplificare la comprensione, il riutilizzo e la manutenzione del codice.  
  
 Usare un diagramma livello per eseguire le attività seguenti:  
  
- Comunicare l'architettura logica esistente o desiderata del sistema.  
  
- Individuare i conflitti tra il codice esistente e l'architettura desiderata.  
  
- Visualizzare l'impatto delle modifiche nell'architettura desiderata in caso di refactoring, aggiornamento o evoluzione del sistema.  
  
- Rafforzare l'architettura desiderata durante lo sviluppo e la manutenzione del codice includendo la convalida con le operazioni di archiviazione e compilazione.  
  
  Questo argomento descrive gli elementi che è possibile usare in un diagramma livello. Per altre informazioni su come creare e tracciare diagrammi livello, vedere [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md). Per altre informazioni sui modelli di livello, visitare il [sito Patterns & Practices](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-layer-diagrams"></a>Lettura di diagrammi livello  
 ![Gli elementi nei diagrammi livello](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")  
  
 La tabella seguente descrive gli elementi che è possibile usare in un diagramma livello.  
  
|**Forma**|**Elemento**|**Descrizione**|  
|---------------|-----------------|---------------------|  
|1|**Livello**|Gruppo logico di elementi fisici nel sistema. Questi elementi possono essere spazi dei nomi, progetti, classi, metodi e così via.<br /><br /> Per visualizzare gli elementi collegati a un livello, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti** per aprire **Esplora livello**.<br /><br /> Per altre informazioni, vedere [Esplora livello](#Explorer).<br /><br /> -   **Non è consentito Namespace dipendenze** -specifica che gli artefatti associati a questo livello non possono dipendere da spazi dei nomi specificati.<br />-   **Forbidden Namespaces** -specifica che gli artefatti associati a questo livello non devono appartenere agli spazi dei nomi specificato.<br />-   **Required Namespaces** -specifica che gli artefatti associati a questo livello devono appartenere a uno degli spazi dei nomi specificati.|  
|2|**dipendenza**|Indica che un livello può usare la funzionalità di un altro livello, ma non viceversa.<br /><br /> -   **Direzione** -specifica la direzione della dipendenza.|  
|3|**Dipendenza bidirezionale**|Indica che un livello può usare la funzionalità di un altro livello e viceversa.<br /><br /> -   **Direzione** -specifica la direzione della dipendenza.|  
|4|**Commentoo**|Usato per aggiungere note generali al diagramma o elementi nel diagramma.|  
|5|**Collegamento commento**|Usato per collegare commenti a elementi nel diagramma.|  
  
##  <a name="Explorer"></a> Esplora livello  
 È possibile collegare ogni livello a elementi nella soluzione, come progetti, classi, spazi dei nomi, file di progetto e altre parti del software. Il numero specificato su un livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretare il numero di elementi in un livello, ricordare quanto segue:  
  
- Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
   Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
- Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
  Per altre informazioni sul collegamento di livelli ed elementi, vedere:  
  
- [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)  
  
- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Per esaminare gli elementi collegati  
  
-   Nel diagramma livello, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**.  
  
     **Esplora livello** apre e visualizza gli elementi che sono collegati ai livelli selezionati. **Esplora livello** include una colonna che mostra ognuna delle proprietà dei collegamenti dell'elemento.  
  
    > [!NOTE]
    >  Se non è possibile visualizzare tutte queste proprietà, espandere la **Esplora livello** finestra.  
  
    |**Colonna in Esplora livello**|**Descrizione**|  
    |----------------------------------|---------------------|  
    |**Categorie**|Tipo di elemento, ad esempio una classe, uno spazio dei nomi, un file di origine e così via|  
    |**Livello**|Livello collegato all'elemento|  
    |**Supporta la convalida**|Se **True**, quindi il processo di convalida dei livelli può verificare che il progetto sia conforme alla dipendenze da o verso questo elemento.<br /><br /> Se **False**, quindi il collegamento non partecipa al processo di convalida dei livelli.<br /><br /> Per altre informazioni, vedere [diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificatore**|Riferimento all'elemento collegato|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)



