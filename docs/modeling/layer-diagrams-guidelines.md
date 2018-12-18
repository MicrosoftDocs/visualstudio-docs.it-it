---
title: 'Diagrammi di dipendenza: Linee guida | Documenti Microsoft'
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
ms.openlocfilehash: 840758b0b370c452ac4428c6bfdad525662ed420
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="dependency-diagrams-guidelines"></a>Diagrammi di dipendenza: linee guida
Vengono descritti l'architettura dell'app a un livello elevato creando *diagrammi dipendenza* in Visual Studio. Assicurarsi che il codice rimanga coerenza con la progettazione convalidando il codice con un diagramma di dipendenze. È anche possibile includere la convalida dei livelli nel processo di compilazione. Vedere [Video di Channel 9: progettazione e convalidare l'architettura con diagrammi di dipendenza](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>Che cos'è un diagramma di dipendenze?  
 Analogamente a un diagramma architettura tradizionale, un diagramma di dipendenze identifica i componenti principali o le unità funzionali della progettazione e le relative interdipendenze. Ogni nodo del diagramma, denominato un *livello*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri elementi. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Vedere [diagrammi dipendenza: riferimento](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a>Come progettare o aggiornare l'applicazione con diagrammi di dipendenza  
 I passaggi seguenti viene fornita una panoramica dell'utilizzo di diagrammi di dipendenza all'interno del processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.  
  
> [!NOTE]
>  I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.  
  
1.  [Creare un diagramma di dipendenza](#Create) per l'intera applicazione o per un livello all'interno di esso.  
  
2.  [Definire i livelli per rappresentare aree funzionali primarie o componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se dispone di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione, è possibile associare ogni livello a una raccolta di *elementi*, ad esempio progetti, spazi dei nomi, file e così via.  
  
3.  [Individuare le dipendenze esistenti](#Generate) tra livelli.  
  
4.  [Modificare i livelli e dipendenze](#EditArchitecture) per mostrare l'aggiornamento che si desidera venga riflessa nel codice di progettazione.  
  
5.  [Progettare nuove aree dell'applicazione](#NewAreas) creando livelli per rappresentare i blocchi di architettura principali o i componenti e definizione di dipendenze per mostrare come ogni livello Usa gli altri.  
  
6.  [Modificare il layout e l'aspetto del diagramma](#EditLayout) per semplificarne l'analisi con i colleghi.  
  
7.  [Convalidare il codice rispetto al diagramma dipendenza](#Validate) per evidenziare i conflitti tra il codice e l'architettura necessaria.  
  
8.  [Aggiornare il codice per conformità alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.  
  
9. [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation) per assicurare che il codice sia sempre conforme alla progettazione.  
  
##  <a name="Create"></a>Creare un diagramma di dipendenza  
 All'interno di un progetto di modellazione, è necessario creare un diagramma di dipendenze. È possibile aggiungere un nuovo diagramma di dipendenza a un progetto di modello esistente, creare un nuovo progetto di modello per il diagramma di dipendenza o copiare un diagramma di dipendenza esistente nello stesso progetto di modellazione.  
  
> [!IMPORTANT]
>  Non aggiungere, trascinare o copiare un diagramma di dipendenza esistente da un progetto di modellazione in un altro progetto di modellazione o in un'altra posizione nella soluzione. Un diagramma di dipendenza che viene copiato in questo modo avranno gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.  
  
 Vedere [creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a>Definire i livelli per rappresentare aree funzionali o componenti  
 I livelli rappresentano gruppi logici di *elementi*, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. È possibile creare livelli da artefatti da progetti Visual c# e Visual Basic oppure è possibile collegare specifiche o piani a un livello collegando documenti, quali file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di artefatti collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.  
  
 È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli elementi sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per informazioni sui modelli di livello, visitare il sito modelli e procedure all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Esistono alcuni tipi di elementi possono essere collegati ai livelli ma che non supportano la convalida rispetto al diagramma della dipendenza. Per verificare se l'elemento supporta la convalida, aprire **Esplora livello** per esaminare il **supporta la convalida** proprietà del collegamento all'elemento. Vedere [individuare le dipendenze esistenti tra livelli](#Generate).  
  
 Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli da Esplora soluzioni con diagrammi di dipendenza. È quindi possibile utilizzare i diagrammi di dipendenza che consentono di aggiornare il codice e mantenerli coerenti con la progettazione.  
  
 Vedere:  
  
-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a>Individuare le dipendenze esistenti tra livelli  
 È presente una dipendenza quando un artefatto associato a un livello dispone di un riferimento a un artefatto associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.  
  
> [!NOTE]
>  Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi sono associate dipendenze che è possibile decompilare, fare doppio clic su uno o più livelli e quindi fare clic su **Visualizza collegamenti**. In **Esplora livello**, esaminare il **supporta la convalida** colonna. Le dipendenze non verranno decompilate per elementi per cui questa colonna viene visualizzato **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli  
  
-   Selezionare uno o più livelli, fare doppio clic su un livello selezionato e quindi fare clic su **genera dipendenze**.  
  
 In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.  
  
##  <a name="EditArchitecture"></a>Modificare livelli e dipendenze per visualizzare la progettazione desiderata  
 Per descrivere le modifiche da apportare al sistema o l'architettura desiderata, utilizzare la procedura seguente per modificare il diagramma di dipendenza. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Vedere [miglioramento della struttura del codice](#Improving).  
  
|**Per**|**Eseguire questi passaggi**|  
|------------|-----------------------------|  
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza e quindi premere **eliminare**.|  
|Modificare o limitare la direzione di una dipendenza|Impostare il relativo **direzione** proprietà.|  
|Creare nuove dipendenze|Utilizzare il **dipendenza** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic su di **puntatore** strumento o premere il **ESC** chiave.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **non è consentito dipendenze Namespace** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
###  <a name="Improving"></a>Miglioramento della struttura del codice  
 Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Codice ben strutturato è una progettazione che è facile astrazione in un diagramma di dipendenze.  
  
 Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.  
  
 Se questo non è il caso, il codice sarà più difficile da modificare per tutta la durata e sarà meno idoneo alla convalida tramite i diagrammi di dipendenza.  
  
##  <a name="NewAreas"></a>Progettare nuove aree dell'applicazione  
 Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.  
  
-   **Mostra i modelli di architettura identificabili** nei diagrammi di dipendenza, se possibile. Ad esempio, un diagramma di dipendenza che descrive un'applicazione desktop potrebbe includere livelli quali presentazione, logica di dominio e archivio dati. Un diagramma di dipendenza che riguarda una singola funzionalità in un'applicazione può includere livelli quali modello, visualizzazione e Controller. Per ulteriori informazioni su tali modelli, vedere [Patterns & Practices: architettura dell'applicazione](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
-   **Creare un elemento di codice per ogni livello** , ad esempio un spazio dei nomi, classe o componente. In questo modo sarà più semplice seguire il codice e collegare gli artefatti di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.  
  
-   **Non è necessario collegare la maggior parte delle classi e altri elementi ai livelli** poiché si trovano in elementi più grandi quali spazi dei nomi che sono già stati collegati ai livelli.  
  
-   **Creare un nuovo diagramma per una nuova funzionalità**. In genere, saranno presenti uno o più diagrammi di dipendenza che descrive l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.  
  
     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.  
  
##  <a name="EditLayout"></a>Modificare il layout per la presentazione e descrizione  
 Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:  
  
-   Modificare le dimensioni, le forme e le posizioni dei livelli.  
  
-   Cambiare i colori dei livelli e le dipendenze.  
  
    -   Selezionare uno o più livelli o dipendenze, pulsante destro del mouse e quindi fare clic su **proprietà**. Nel **proprietà** finestra, modificare il **colore** proprietà.  
  
##  <a name="Validate"></a>Convalidare il codice rispetto al diagramma  
 Dopo avere modificato il diagramma, sarà possibile convalidarlo manualmente rispetto al codice in qualsiasi momento oppure automaticamente ogni volta che si esegue una compilazione locale o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].  
  
 Vedere:  
  
-   [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)  
  
##  <a name="UpdateCode"></a>Aggiornare il codice per conformità alla nuova architettura  
 In genere, la prima volta che è convalidare il codice in base a un diagramma di dipendenze aggiornato vengono visualizzati errori. Gli errori possono avere cause diverse:  
  
-   Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.  
  
-   Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.  
  
 Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per ulteriori informazioni su questi errori, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Quando si sviluppa o il refactoring del codice, potrebbe essere nuovi artefatti da collegare al diagramma di dipendenza. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.  
  
 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Per eseguire questa attività, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a>Includere la convalida dei livelli nel processo di compilazione  
 Per assicurarsi che le modifiche future al codice siano conformi ai diagrammi dipendenza, includere la convalida dei livelli per il processo di compilazione standard della soluzione. Quando altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma di dipendenze verranno segnalate come errori di compilazione. Per ulteriori informazioni sull'inclusione di convalida dei livelli nel processo di compilazione, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
