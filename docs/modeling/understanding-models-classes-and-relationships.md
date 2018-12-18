---
title: Informazioni sui modelli, classi e relazioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c0e2faf70c6d5857d967fc26e88242c54ea9906f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="understanding-models-classes-and-relationships"></a>Informazioni su modelli, classi e relazioni
Un linguaggio specifico di dominio (DSL) viene definito dal relativo file di definizione DSL, insieme a qualsiasi codice programma personalizzato che è possibile scrivere. La maggior parte del codice programma nella soluzione DSL viene generato da questo file.  
  
 In questo argomento illustra le funzionalità centrale della definizione DSL.  
  
## <a name="the-dsl-definition"></a>La definizione DSL  
 Quando si apre `Dsl\DslDefinition.dsl`, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finestra simile nell'immagine seguente.  
  
 ![Progettazione DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Le informazioni più importanti nella definizione DSL viene visualizzate nel diagramma definizione DSL. Informazioni aggiuntive, che fa anche parte di DslDefinition.dsl, viene visualizzate in Esplora DSL, che in genere viene visualizzata sul lato del diagramma. È possibile utilizzare con il diagramma per le operazioni più frequenti che con Esplora DSL per le personalizzazioni più avanzate.  
  
 Il diagramma della definizione DSL vengono illustrate le classi di dominio che definiscono gli elementi del modello e le relazioni che definiscono i collegamenti tra elementi del modello. Viene inoltre le forme e connettori che consentono di visualizzare gli elementi del modello per l'utente.  
  
 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Quando si seleziona un elemento nella definizione del linguaggio DSL, nel diagramma o in Esplora DSL, informazioni su di esso viene visualizzate nella finestra Proprietà. Informazioni aggiuntive, verrà visualizzate nella finestra Dettagli DSL.  
  
### <a name="models-are-instances-of-dsls"></a>I modelli sono istanze di DSL  
 Oggetto *modello* è un'istanza di tale linguaggio DSL creato da un utente. Un modello contiene gli elementi del modello, che sono istanze di classi di dominio che definiscono e collegamenti tra gli elementi, che sono istanze di che definiscono le relazioni di dominio. Un modello può inoltre avere forme e connettori, che consentono di visualizzare gli elementi di modello e i collegamenti in un diagramma. La definizione DSL include le classi di forma, classi connettore e una classe per il diagramma.  
  
 Una definizione DSL è noto anche come un *modello di dominio*. Un modello di dominio o definizione DSL è la rappresentazione in fase di progettazione del linguaggio specifico di dominio, mentre il modello è la creazione dell'istanza di runtime del linguaggio specifico di dominio.  
  
## <a name="domain-classes-define-model-elements"></a>Le classi di dominio definiscono gli elementi del modello  
 Classi di dominio vengono utilizzate per creare i vari elementi nel dominio e le relazioni di dominio sono i collegamenti tra gli elementi. Sono la rappresentazione in fase di progettazione degli elementi e i collegamenti che verranno creati dagli utenti del linguaggio specifico di progettazione quando si creano i relativi modelli.  
  
 Questa illustrazione mostra un modello che è stato creato dall'utente di un catalogo musicale DSL. Album musicali sono rappresentati da caselle che contengono elenchi di brani. Artisti sono rappresentati da caselle arrotondati e sono connessi gli album a cui essi hanno contribuito.  
  
 ![Modello di istanza generato DSL](../modeling/media/music_instance.png "Music_Instance")  
  
 La definizione DSL separa due aspetti. L'aspetto degli elementi del modello del diagramma del modello viene definito tramite le classi di forma e connettore. Le informazioni contenute nel modello sono definite tramite relazioni di dominio e le classi di dominio.  
  
 Nella figura seguente mostra le classi di dominio e le relazioni nella definizione DSL di musicale.  
  
 ![Le relazioni di incorporamento e riferimento](../modeling/media/music_classes.png "Music_Classes")  
  
 La figura sono illustrate quattro classi di dominio: musica, Album, artista e canzone. Le classi di dominio definiscono le proprietà di dominio, ad esempio nome, titolo e così via. Nel modello di istanza, i valori di alcune di queste proprietà vengono visualizzati nel diagramma.  
  
 Tra le classi sono relazioni di dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs e ArtistAppearedOnAlbums. Le relazioni dispongono di molteplicità, ad esempio 1..1, 0... *. Ad esempio, ogni canzone deve essere correlato a un solo Album tramite la relazione AlbumHasSongs. Ogni Album può avere un numero qualsiasi di brani.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Ridisposizione il diagramma della definizione DSL  
 Si noti che una classe di dominio può venire visualizzato diverse volte nel diagramma definizione DSL, come nell'immagine Album. È sempre presente una visualizzazione principale e possono essere presenti alcune *riferimento* viste.  
  
 Per ridisporre il diagramma della definizione DSL, è possibile:  
  
-   Scambio principale e fare riferimento alle viste tramite il **portare albero qui** e **della struttura di suddivisione** comandi. Fare doppio clic su una classe di dominio singolo per visualizzare questi comandi.  
  
-   Riordinare le classi di dominio e le classi di forma premendo Ctrl + freccia su e Ctrl + freccia giù.  
  
-   Comprimere o espandere classi utilizzando l'icona in alto a destra di ciascuna forma.  
  
-   Comprimere parti della struttura ad albero, fare clic sul segno meno (-) nella parte inferiore di una classe di dominio.  
  
## <a name="inheritance"></a>Ereditarietà  
 Classi di dominio possono essere definite utilizzando l'ereditarietà. Per creare una derivazione di ereditarietà, fare clic sullo strumento di ereditarietà, la classe derivata, scegliere la classe di base. Un elemento del modello include tutte le proprietà che sono definite nella propria classe di dominio, insieme a tutte le proprietà ereditate dalla classe di base. Eredita anche i ruoli nelle relazioni.  
  
 Ereditarietà può anche essere usata tra relazioni, forme e connettori. Ereditarietà deve mantenere nello stesso gruppo. Una forma non può ereditare da una classe di dominio.  
  
## <a name="domain-relationships"></a>Relazioni di dominio  
 Gli elementi del modello possono essere collegati tramite relazioni. I collegamenti sempre sono binari; Collega esattamente due elementi. Tuttavia, qualsiasi elemento può avere molti collegamenti ad altri oggetti, e può anche essere più di un collegamento tra la stessa coppia di elementi.  
  
 Come è possibile definire diverse classi di elementi, è possibile definire diverse classi di collegamenti. La classe di un collegamento viene chiamata un *relazione dominio*. Una relazione di dominio specifica quali classi dell'elemento in cui è possono connettere le istanze. Viene chiamato ogni estremità di una relazione di un *ruolo*, e la relazione di dominio definisce i nomi per i due ruoli, nonché per la relazione stessa.  
  
 Esistono due tipi di relazioni di dominio: incorporamento di relazioni e le relazioni di riferimento. Sul diagramma della definizione DSL, le relazioni di incorporamento hanno linee continue in ogni ruolo e relazioni di riferimento sono tratteggiate.  
  
### <a name="embedding-relationships"></a>Incorporamento di relazioni  
 Ogni elemento in un modello, ad eccezione di radice, è la destinazione di un collegamento di incorporamento. Pertanto, l'intero modello costituisce una singola struttura di collegamenti di incorporamento. Una relazione di incorporamento rappresenta contenuto o della proprietà. Due elementi del modello che sono correlati in questo modo sono anche noti come padre e figlio. L'elemento figlio viene definito da incorporare nell'elemento padre.  
  
 Incorporamento di collegamenti non vengono in genere visualizzati in modo esplicito come connettori in un diagramma. In alternativa, in genere sono rappresentati dal contenuto. La radice del modello è rappresentata dal diagramma e gli elementi incorporati in essa contenuti vengono visualizzati come forme nel diagramma.  
  
 Nell'esempio, la classe radice musica ha una relazione di incorporamento MusicHasAlbums ad Album, che ha un AlbumHasSongs di incorporamento per canzone. Brani vengono visualizzati come elementi in un elenco all'interno di ogni Album. Musica ha anche un MusicHasArtists incorporamento alla classe artista, le cui istanze sono anche visualizzate come forme nel diagramma.  
  
 Per impostazione predefinita, gli elementi incorporati vengono eliminati automaticamente quando vengono eliminati i relativi elementi padre.  
  
 Quando viene salvato un modello di file in formato XML, gli elementi incorporati annidati all'interno di elementi padre, a meno che non è stato personalizzato della serializzazione.  
  
> [!NOTE]
>  L'incorporamento è diverso dall'ereditarietà. Gli elementi figlio in una relazione di incorporamento non ereditano le proprietà dell'elemento padre. Un tipo di incorporamento è un tipo di collegamento tra gli elementi del modello. Ereditarietà è una relazione tra classi e creare collegamenti tra elementi del modello.  
  
### <a name="embedding-rules"></a>Incorporamento di regole  
 Ogni elemento in un modello di istanza deve essere la destinazione di un solo collegamento incorporamento, tranne la radice del modello.  
  
 Pertanto, ogni classe di dominio non astratta, ad eccezione della classe principale, deve essere la destinazione di almeno una relazione di incorporamento, o deve ereditare un incorporamento da una classe base. Una classe può essere la destinazione degli incorporamenti di due o più, ma gli elementi del modello relativa istanza possono avere un solo padre alla volta. La molteplicità dalla destinazione all'origine deve essere 0..1 1 o 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>Esplora risorse consente di visualizzare la struttura ad albero di incorporamento  
 La definizione DSL crea inoltre un elenco di cartelle, gli utenti vedono insieme ai relativi diagramma del modello.  
  
 ![Finestra di esplorazione generata di DSL](../modeling/media/music_explorer.png "Music_Explorer")  
  
 Esplora risorse Mostra tutti gli elementi nel modello, anche quelli per cui non è stata definita alcuna forma. Mostra elementi e relazioni di incorporamento, ma non fare riferimento a relazioni.  
  
 Per visualizzare i valori delle proprietà del dominio di un elemento, l'utente seleziona un elemento del diagramma del modello o in Esplora modelli e viene visualizzata la finestra Proprietà. Visualizza tutte le proprietà di dominio, inclusi quelli che non vengono visualizzati nel diagramma. Nell'esempio dispone di un titolo e un genere ogni canzone, ma nel diagramma viene visualizzato solo il valore del titolo.  
  
## <a name="reference-relationships"></a>Relazioni di riferimento  
 Una relazione di riferimento rappresenta qualsiasi tipo di relazione che non è l'incorporamento.  
  
 Relazioni di riferimento vengono in genere visualizzate in un diagramma come connettori tra le forme.  
  
 Nella rappresentazione XML del modello, un collegamento di riferimento tra due elementi viene rappresentato con *moniker.* Vale a dire i moniker sono nomi che identificano in modo univoco ogni elemento del modello. Il nodo XML per ogni elemento del modello contiene un nodo che specifica il nome della relazione e il moniker di altro elemento.  
  
## <a name="roles"></a>Ruoli  
 Ogni relazione di dominio ha due ruoli, un ruolo di origine e un ruolo di destinazione.  
  
 Nell'immagine seguente, la riga tra il **Publisher** classe di dominio e **PublisherCatalog** relazione di dominio è il ruolo di origine. La riga tra la relazione di dominio e **Album** classe di dominio è il ruolo di destinazione.  
  
 ![Ruoli e le proprietà. ] (../modeling/media/propertycode.png "PropertyCode")  
  
 I nomi associati a una relazione sono particolarmente importanti quando si scrive codice programma che attraversa il modello. Ad esempio, quando si compila la soluzione DSL, la classe generata, server di pubblicazione ha una proprietà del catalogo che è una raccolta di album. La classe Album ha una proprietà server di pubblicazione che è una singola istanza della classe server di pubblicazione.  
  
 Quando si crea una relazione in una definizione DSL, i nomi di proprietà e relazioni sono valori predefiniti specificati. Tuttavia, è possibile modificarle.  
  
## <a name="multiplicities"></a>Molteplicità  
 Molteplicità specificare quanti elementi possa avere lo stesso ruolo in una relazione di dominio. Nell'esempio zero-a-molti (0...\*) impostazione molteplicità di **catalogo** ruolo specifica che qualsiasi istanza del **Publisher** classe di dominio può avere un numero  **PublisherCatalog** relazione collegamenti che si desidera assegnare.  
  
 Configurare la molteplicità di un ruolo digitando nel diagramma o modificando il `Multiplicity` proprietà il **proprietà** finestra. Nella tabella seguente descrive le impostazioni per questa proprietà.  
  
|Tipo di valore di molteplicità|Descrizione|  
|-----------------------|-----------------|  
|0... * (da zero a molti)|Ogni istanza della classe di dominio può avere più istanze della relazione o alcuna istanza della relazione.|  
|0..1 (da zero a uno)|Ogni istanza della classe di dominio può avere contemporaneamente più istanze della relazione o alcuna istanza della relazione.|  
|1..1 (uno)|Ogni istanza della classe di dominio può avere un'istanza della relazione. È possibile creare più di un'istanza di questa relazione da qualsiasi istanza della classe ruolo. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando qualsiasi istanza della classe ruolo non dispone di alcuna istanza della relazione.|  
|1... * (da uno a molti)|Ogni istanza della classe sul ruolo che ha questo molteplicità può avere più istanze della relazione e ogni istanza deve avere almeno un'istanza della relazione. Se la convalida è abilitata, verrà visualizzato un errore di convalida quando qualsiasi istanza della classe ruolo non dispone di alcuna istanza della relazione.|  
  
## <a name="domain-relationships-as-classes"></a>Relazioni di dominio come classi  
 Un collegamento è rappresentato nell'archivio come un'istanza di LinkElement, ovvero una classe derivata di ModelElement. Il diagramma del modello di dominio alle relazioni di dominio, è possibile definire queste proprietà.  
  
 È possibile impostare una relazione di origine o di destinazione di altre relazioni. Nel diagramma del modello di dominio, il pulsante destro la relazione di dominio e quindi fare clic su **Mostra come classe**. Verrà visualizzata una finestra di classi aggiuntive. È quindi possibile connettere le relazioni a esso.  
  
 È possibile definire una relazione in parte dall'ereditarietà, proprio come con le classi di dominio. Selezionare la relazione derivata e impostare **relazione Base** nella finestra Proprietà.  
  
 Una relazione derivata specializza la relazione di base. Classi di dominio che devono essere derivati da collegamenti o lo stesso come le classi collegate tramite la relazione di base. Quando viene creato un collegamento della relazione derivata in un modello, è un'istanza della classe derivata sia le relazioni di base. Nel codice programma, è possibile spostarsi all'estremità opposta del collegamento utilizzando le proprietà generate dal tipo di base o dalla classe derivata.  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
