---
title: Utilizzo del diagramma della definizione DSL | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 603189cdc4ac65c4b12fae0e736025b622765c81
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="working-with-the-dsl-definition-diagram"></a>Utilizzo del diagramma di definizione DSL
Il diagramma di un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definizione è uno strumento importante per la definizione di linguaggio specifico di dominio. Consente di aggiungere elementi al modello di dominio e definire relazioni sul diagramma ed è possibile modificare il layout del diagramma per renderlo più leggibile.  
  
## <a name="the-layout-of-the-diagram"></a>Layout del diagramma  
 Il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definizione diagramma dispone di due partizioni, la **classi e relazioni** partizione e **elementi del diagramma** partizione. Il **classi e relazioni** partizione consente di visualizzare le classi di dominio, relazioni di dominio e l'ereditarietà. Il **elementi del diagramma** partizione consente di visualizzare le classi di forma, connettore classi, classi corsia e il diagramma di progettazione generato.  
  
 Classi di dominio possono essere visualizzati in più posizioni di **classi e relazioni** partizioni. In una definizione di classe di dominio viene visualizzato un albero di ereditarietà se si tratta della classe di base per altre classi di dominio e un albero delle relazioni se si tratta dell'origine delle relazioni di incorporamento o riferimento. I segnaposto delle classi di dominio vengono visualizzati come le destinazioni delle relazioni di incorporamento o riferimento. Per impostazione predefinita, vengono visualizzati gli elementi di segnaposto con il **proprietà dominio** raggruppamento compresso. Per questi elementi, non vengono mostrati l'ereditarietà o le relazioni di incorporamento o riferimento.  
  
 Quando si aggiunge una classe di dominio, viene visualizzato nella parte inferiore del **classi e relazioni** partizione. Quando si aggiunge una relazione di incorporamento o riferimento, questa viene posizionata a destra sotto la classe di dominio di origine.  
  
 Man mano che si aggiungono classi e relazioni di dominio, può risultare difficile individuare una classe di dominio specifica. È possibile trovare una classe di dominio facendo clic su esso nel **Esplora DSL** e quindi fare clic su **individua nel diagramma**.  
  
 Nelle sezioni seguenti viene descritto come modificare l'aspetto del diagramma per renderlo più leggibile.  
  
## <a name="copying-elements"></a>Copia di elementi  
 È possibile usare i comandi Copia, Taglia e Incolla sugli elementi nel diagramma della definizione DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Zoom avanti o indietro sul diagramma  
 È possibile ingrandire e rimpicciolire il diagramma utilizzando le **Progettazione DSL** barra degli strumenti per impostare il livello di zoom.  
  
## <a name="hiding-map-lines"></a>Nascondere linee mappa  
 Le linee mappa sono linee tracciate tra una classe di dominio o una relazione di dominio e la forma o il connettore a cui è mappata. È possibile nascondere linee mappa facendo il **Mostra righe mappa** pulsante il **Progettazione DSL** barra degli strumenti. Per visualizzare le linee, fare di nuovo clic sul pulsante.  
  
## <a name="changing-the-diagram-layout"></a>Modifica del layout del diagramma  
 È possibile modificare il layout del **classi e relazioni** partizione come indicato di seguito.  
  
### <a name="expandcollapse"></a>Expand/Collapse  
 È possibile ridurre le dimensioni di un elemento di raggruppamento forma che rappresenta una classe di dominio o una forma facendo clic destro e quindi facendo clic su **Comprimi**. In tal modo il **proprietà dominio** raggruppamento della forma. Per visualizzare il **proprietà dominio** raggruppamento nuovamente, fare clic sulla forma e quindi fare clic su **Espandi**.  
  
### <a name="move-updown"></a>Move Up/Move Down  
 È possibile spostare una dominio classe o diagramma di un elemento verso l'alto o verso il basso nella partizione facendo clic l'elemento e quindi fare clic su **Sposta su** o **Sposta giù**. Se si sposta un elemento segnaposto visualizzato come destinazione di una relazione di incorporamento o riferimento, la relazione verrà spostata insieme all'elemento.  
  
### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree  
 Se una classe di dominio svolge il ruolo di origine nelle relazioni di incorporamento o un riferimento con altre classi di dominio, è possibile nascondere le relazioni facendo clic la definizione di classe di dominio e quindi fare clic su **Comprimi relazioni albero**. Per visualizzare le relazioni, il pulsante destro l'elemento della definizione e quindi fare clic su **espandere struttura ad albero di relazioni**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree  
 Se una classe di dominio è la classe di base di altre classi di dominio, è possibile nascondere l'albero di ereditarietà facendo clic la definizione di classe di dominio e quindi fare clic su **albero di ereditarietà Comprimi**. Per visualizzare l'albero di ereditarietà, il pulsante destro l'elemento della definizione e quindi fare clic su **espandere albero di ereditarietà**.  
  
### <a name="bring-tree-here"></a>Bring Tree Here  
 È possibile consolidare il diagramma facendo clic su una classe di dominio segnaposto e scegliendo **portare albero qui**. La classe di dominio segnaposto diventa un elemento della definizione e visualizza gli alberi di ereditarietà e delle relazioni. L'elemento della definizione precedente diventa un elemento segnaposto se costituisce la destinazione di una relazione o l'elemento figlio in una relazione di ereditarietà; in caso contrario, non viene più visualizzato.  
  
### <a name="split-tree"></a>Split Tree  
 È possibile interrompere le strutture ad albero di ereditarietà o relazioni facendo clic sulla definizione di classe dominio che li visualizza e quindi facendo clic su **della struttura di suddivisione**. L'elemento della definizione diventa un elemento segnaposto e la classe di dominio della definizione, insieme ai relativi alberi di ereditarietà e delle relazioni, è ora visualizzata nella parte inferiore della partizione.  
  
### <a name="show-as-class"></a>Show As Class  
 Se le relazioni è derivata da una relazione di dominio, o se dispone di incorporamento o riferimento relazioni con altre relazioni di dominio, è possibile visualizzare la relazione come classe facendo clic sulla relazione e quindi facendo clic su **Mostra come classe** . Verrà visualizzata la relazione con un **proprietà dominio** raggruppamento e verranno visualizzati gli alberi di ereditarietà e le relazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)