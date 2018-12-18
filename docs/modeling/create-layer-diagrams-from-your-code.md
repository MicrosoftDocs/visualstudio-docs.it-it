---
title: Creare diagrammi dipendenza dal codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
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
ms.openlocfilehash: 18477479255ff7af8216d093830c6c0d60fa50dc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="create-dependency-diagrams-from-your-code"></a>Creare diagrammi dipendenza dal codice

Per visualizzare l'architettura di alto livello, logica del sistema software, creare un *diagramma dipendenze* in Visual Studio. Per assicurarsi che il codice rimanga coerenza con la progettazione, è possibile convalidare il codice con un diagramma di dipendenze. È possibile creare diagrammi di dipendenza per i progetti Visual c# e Visual Basic. Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

![Creare un diagramma di dipendenza](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

Un diagramma di dipendenza consente di organizzare gli elementi di soluzione di Visual Studio in gruppi logici e astratti denominati *livelli*. È possibile utilizzare i livelli per descrivere le attività principali che tali artefatti eseguono oppure i componenti principali del sistema. Ogni livello può contenere altri livelli che descrivono attività più dettagliate. È inoltre possibile specificare l'esistenti o *dipendenze* tra livelli. Tali dipendenze, rappresentate come frecce, mostrano quali livelli possono utilizzare o utilizzano attualmente la funzionalità rappresentata da altri livelli. Per gestire controllo a livello di architettura nel codice, mostrare le dipendenze desiderate nel diagramma, quindi convalidare il codice in base al diagramma.

[Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

##  <a name="CreateDiagram"></a>Creare un diagramma di dipendenza

Prima di creare un diagramma di dipendenze, assicurarsi che la soluzione contiene un progetto di modellazione.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare un diagramma di dipendenza esistente da un progetto di modellazione in un altro progetto di modellazione o in un'altra posizione nella soluzione. In questo modo i riferimenti del diagramma originale verranno mantenuti, anche se si modifica il diagramma. In caso contrario, il funzionamento della convalida dei livelli non sarà corretto e potrebbero verificarsi altri problemi, quali la mancanza di elementi o altri errori quando si tenta di aprire il diagramma.
>
> In alternativa, è possibile aggiungere un nuovo diagramma di dipendenza al progetto di modello. copiare gli elementi dal diagramma di origine al nuovo diagramma Salvare il progetto di modello sia il nuovo diagramma di dipendenza.

#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Per aggiungere un nuovo diagramma di dipendenza a un progetto di modellazione  
  
1.  Nel **architettura** menu, scegliere **nuovo diagramma dipendenza**.  
  
2.  In **modelli**, scegliere **diagramma dipendenza**.  
  
3.  Assegnare un nome al diagramma.  
  
4.  In **aggiungere al progetto di modello**, individuare e selezionare un progetto di modello esistente nella soluzione.  
  
     oppure  
  
     Scegliere **creare un nuovo progetto di modellazione** per aggiungere un nuovo progetto di modellazione per la soluzione.  
  
    > [!NOTE]
    >  Il diagramma dipendenza deve esistere all'interno di un progetto di modellazione. È tuttavia possibile collegarlo a elementi in qualsiasi punto della soluzione.  
  
5.  Assicurarsi di salvare il progetto di modello sia il diagramma di dipendenze.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Trascinare e rilasciare, oppure copiare e incollare, da una mappa del codice

1. Generare una mappa del codice per la soluzione usando il **architettura** menu. 

2. È possibile applicare un filtro mappa del codice per rimuovere le cartelle della soluzione e "Test risorse" Se si desidera applicare le dipendenze nel codice di prodotto.

3. Nella mappa del codice generato, rimuovere il nodo "Esterno", o espandere in modo da visualizzare gli assembly esterni, a seconda che si desideri applicare dipendenze dello spazio dei nomi e quindi eliminare assembly non necessari dalla mappa del codice. 

4. Creare un nuovo diagramma di dipendenza per la soluzione usando il **architettura** menu

5. Selezionare tutti i nodi nella mappa del codice (utilizzare _Ctrl_ + _A_, o utilizzare il rettangolo di selezione premendo il _MAIUSC_ chiave prima di fare clic su, trascinare e rilasciare.

6. Trascinamento e rilascio, o una copia e Incolla, gli elementi selezionati al nuovo diagramma di convalida della dipendenza. 

7. Mostra l'architettura dell'applicazione corrente. Stabilire l'architettura da desiderato e modificare di conseguenza il diagramma di dipendenze.

![Diagramma di dipendenze generato da una mappa del codice](media/dependency-validation-01.png)
  
##  <a name="CreateLayers"></a>Creare livelli da artefatti  
 È possibile creare livelli da elementi presenti in una soluzione di Visual Studio, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. In questo modo vengono creati automaticamente collegamenti tra livelli ed elementi, che vengono inclusi nel processo di convalida dei livelli.  
  
 È inoltre possibile collegare livelli a elementi che non supportano la convalida, ad esempio documenti Word o presentazioni PowerPoint, in modo da associare un livello con specifiche o piani. È anche possibile collegare livelli a file di progetti condivisi tra più applicazioni, ma il processo di convalida non includerà tali livelli, che vengano visualizzati con nomi generici come "Livello 1" e "Livello 2".  
  
 Per verificare se un elemento collegato supporta la convalida, aprire **Esplora livello** ed esaminare il **supporta la convalida** proprietà dell'elemento. Vedere [la gestione dei collegamenti agli elementi](#Managing).  
  
|**Per**|**Seguire questi passaggi**|  
|------------|----------------------------|  
|Creare un livello per un solo artefatto|<ol><li>Trascinare l'elemento nel diagramma dipendenza da queste origini:<br /><br /> <ul><li>**Esplora soluzioni**<br /><br />         Ad esempio, è possibile trascinare file o progetti.</li><li>Mappe codice<br /><br />         Vedere [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) e [usare le mappe codici per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Visualizzazione classi** o **Visualizzatore oggetti**</li></ul><br />     Nel diagramma viene visualizzato un livello collegato all'artefatto.</li><li>Rinominare il livello per riflettere le responsabilità del codice o degli artefatti associati.</li></ol> **Importante:** trascinando i file binari per il diagramma di dipendenze non vengono aggiunti automaticamente i riferimenti al progetto di modello. ma è necessario aggiungere manualmente i file binari desiderati per convalidare il progetto di modellazione. **Per aggiungere i file binari al progetto di modello** <ol><li>In **Esplora**, aprire il menu di scelta rapida per il progetto di modello e quindi scegliere **Aggiungi elemento esistente**.</li><li>Nel **Aggiungi elemento esistente** nella finestra di dialogo selezionare i file binari, selezionarli e quindi scegliere **OK**.     I file binari verranno visualizzati nel progetto di modellazione.</li><li>In **Esplora**, scegliere un file binario aggiunto e quindi premere **F4** per aprire la **proprietà** finestra.</li><li>Per ogni file binario, impostare il **azione di compilazione** proprietà **convalida**.</li></ol>|  
|Creare un solo livello per tutti gli artefatti selezionati|Trascinare contemporaneamente tutti gli elementi nel diagramma di dipendenza.<br /><br /> Nel diagramma viene visualizzato un livello collegato a tutti gli artefatti.|  
|Creare un livello per ogni artefatto selezionato|Premere e tenere premuto il **MAIUSC** mentre si trascinano contemporaneamente tutti gli elementi nel diagramma di dipendenza. **Nota:** se si utilizza il **MAIUSC** per selezionare un intervallo di elementi, rilasciare il tasto dopo avere selezionato gli elementi. Premerlo e tenerlo premuto nuovamente quando si trascinano gli artefatti nel diagramma. <br /><br /> Per ogni elemento nel diagramma viene visualizzato un livello collegato a ciascun elemento.|  
|Aggiungere un elemento a un livello|Trascinare l'elemento sul livello.|  
|Creare un nuovo livello non collegato|Nel **della casella degli strumenti**, espandere il **dipendenza diagramma** sezione e quindi trascinare un **livello** nel diagramma di dipendenza.<br /><br /> Per aggiungere più livelli, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** strumento o premere il **ESC** chiave.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il diagramma di dipendenza, scegliere **Aggiungi**, quindi scegliere **livello**.|  
|Creare livelli annidati|Trascinare un livello esistente su un altro livello.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per un livello, scegliere **Aggiungi**, quindi scegliere **livello**.|  
|Creare un nuovo livello contenente due o più livelli esistenti|Selezionare i livelli, aprire il menu di scelta rapida per la selezione e quindi scegliere **gruppo**.|  
|Modificare il colore di un livello|Impostare il relativo **colore** proprietà sul colore desiderato.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **non è consentito dipendenze Namespace** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
 Il numero raffigurato sul livello indica il numero di artefatti a esso collegati. Tuttavia, nell'interpretazione di tale numero, considerare quanto segue:  
  
-   Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
-   Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
##  <a name="Managing"></a>Gestire collegamenti tra livelli ed elementi  
  
1.  Nel diagramma di dipendenza, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti**.  
  
     **Esplora livello** vengono visualizzati i collegamenti di artefatto per il livello selezionato.  
  
2.  Usare le seguenti attività per gestire tali collegamenti:  
  
|**Per**|**In Esplora livello**|  
|------------|---------------------------|  
|Eliminare il collegamento tra il livello e un artefatto|Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **eliminare**.|  
|Spostare il collegamento da un livello a un altro|Trascinare il collegamento dell'elemento in un livello esistente del diagramma.<br /><br /> -oppure-<br /><br /> 1.  Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **Taglia**.<br />2.  Nel diagramma di dipendenza, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Copiare il collegamento da un livello a un altro|1.  Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **copia**.<br />2.  Nel diagramma di dipendenza, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Creare un nuovo livello da un collegamento dell'artefatto esistente|Trascinare il collegamento dell'artefatto in un'area vuota del diagramma.|  
|Verificare che un elemento collegato supporti la convalida rispetto al diagramma della dipendenza.|Esaminare il **supporta la convalida** colonna per il collegamento dell'elemento.|  
  
##  <a name="Discovering"></a>Decompilare dipendenze esistenti  
 È presente una dipendenza quando un artefatto associato a un livello dispone di un riferimento a un artefatto associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. È possibile decompilare dipendenze esistenti per elementi collegati a livelli nel diagramma.  
  
> [!NOTE]
>  Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi sono associate dipendenze che è possibile decompilare, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**. In **Esplora livello**, esaminare il **supporta la convalida** colonna. Le dipendenze non verranno decompilate per elementi per cui questa colonna viene visualizzato **False**.  
  
-   Selezionare uno o più livelli, aprire il menu di scelta rapida per un livello selezionato e quindi scegliere **genera dipendenze**.  
  
 In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.  
  
##  <a name="EditDependencies"></a>Modificare livelli e dipendenze per visualizzare la progettazione desiderata  
 Per descrivere le modifiche da apportare al sistema o l'architettura desiderata, modificare il diagramma di dipendenze:  
  
|**Per**|**Eseguire questi passaggi**|  
|------------|-----------------------------|  
|Modificare o limitare la direzione di una dipendenza|Impostare il relativo **direzione** proprietà.|  
|Creare nuove dipendenze|Utilizzare il **dipendenza** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** strumento o premere il **ESC** chiave.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **non è consentito dipendenze Namespace** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
##  <a name="EditLayout"></a>Modificare la modalità con cui gli elementi vengono visualizzati nel diagramma  
 È possibile modificare la dimensione, la forma, il colore e la posizione dei livelli o il colore delle dipendenze modificandone le proprietà.  
  
##  <a name="Codemaps"></a>Individuare i modelli e le dipendenze da una mappa del codice  
 Durante la creazione di diagrammi di dipendenza, è possibile creare **mappe del codice**. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti per esplorare assembly, spazi dei nomi e classi, che spesso corrispondono ai livelli esistenti. Per altre informazioni sulle mappe codice, vedere:  
  
-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualizzare il codice](../modeling/visualize-code.md)
