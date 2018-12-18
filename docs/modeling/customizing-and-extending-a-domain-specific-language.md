---
title: Personalizzazione ed estensione di un linguaggio specifico di dominio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7617deb73ecaec835b0100d243b75bc26fd54a17
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizzazione ed estensione di un linguaggio specifico di dominio
Visual Studio di modellazione e SDK di visualizzazione (VMSDK) garantisce livelli diversi in cui è possibile definire gli strumenti di modellazione seguenti:  
  
1.  Definire un linguaggio specifico di dominio (DSL) utilizzando il diagramma della definizione DSL. È possibile creare rapidamente un linguaggio DSL con una notazione di diagramma, un formato leggibile XML e gli strumenti di base necessarie per generare il codice e altri elementi.  
  
     Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Utilizzo delle funzionalità più avanzate della definizione DSL ottimizzare del linguaggio DSL. Ad esempio, è possibile visualizzare collegamenti aggiuntivi quando l'utente crea un elemento. Queste tecniche sono principalmente ottenute nella definizione del linguaggio DSL, mentre altri richiedono alcune righe di codice programma.  
  
3.  Estendere gli strumenti di modellazione tramite codice programma. VMSDK è progettato in modo specifico per facilitare l'integrazione delle estensioni con il codice generato dalla definizione DSL.  Per ulteriori informazioni, vedere [scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Dopo aver aggiornato il file di definizione DSL, non dimenticare di fare clic su **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni, prima di ricompilare la soluzione.  
  
##  <a name="customShapes"></a>In questa sezione  
  
|Per ottenere questo risultato|Fare riferimento a questo argomento|  
|----------------------------|-------------------------|  
|Consentire all'utente di impostare le proprietà del colore e lo stile di una forma.|Il pulsante destro della forma o il connettore di classe, scegliere **aggiungere esposti**, fare clic su un elemento.<br /><br /> Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Diverse classi di elemento del modello è simile nel diagramma, condividendo le proprietà, ad esempio l'altezza iniziale e la larghezza, colore, le descrizioni comandi.|Utilizzare l'ereditarietà tra le forme o classi connettore. I mapping tra le forme derivate e le classi derivate di dominio ereditano i dettagli di mapping di elementi padre.<br /><br /> In alternativa, eseguire il mapping delle classi di dominio diverso alla stessa classe di forma.|  
|Una classe di elemento del modello viene visualizzata per contesti di forme diverse.|Eseguire il mapping di più di una classe forma alla stessa classe di dominio. Quando si compila la soluzione, seguire la segnalazione errori e fornire il codice richiesto per decidere quale forma da utilizzare.|  
|Colore della forma o altre funzionalità, ad esempio tipo di carattere indicano lo stato corrente.|Vedere [aggiornare forme e connettori in modo da riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Creare una regola che aggiorna le proprietà esposte. Vedere [regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> In alternativa, utilizzare OnAssociatedPropertyChanged() per aggiornare funzionalità non esposti come collegamento frecce o tipo di carattere.|  
|Icona alle modifiche di forma per indicare lo stato.|Impostare la visibilità del mapping decorator nella finestra Dettagli DSL. Individuare gli elementi Decorator immagine di diversi nella stessa posizione. Vedere [aggiornare forme e connettori in modo da riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> In alternativa, eseguire l'override `ImageField.GetDisplayImage()`. Vedere l'esempio in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Impostare un'immagine di sfondo per qualsiasi forma|Eseguire l'override InitializeInstanceResources() per aggiungere un ImageField ancorata. Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Annidare forme a qualsiasi profondità|Consente di impostare una ricorsiva incorporamento di struttura ad albero. Definire BoundsRules per contenere le forme. Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Collegare i connettori in punti predefiniti del limite dell'elemento.|Definire gli elementi incorporati terminali, rappresentati da porte di piccole dimensioni nel diagramma. Usare BoundsRules per risolvere le porte sul posto. Vedere l'esempio di diagramma circuito in [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Campo di testo consente di visualizzare un valore derivato da altri valori.|Eseguire il mapping l'elemento decorator testo a una proprietà dominio calcolata o di archiviazione personalizzato. Per ulteriori informazioni, vedere [calcolate e le proprietà di archiviazione personalizzato](../modeling/calculated-and-custom-storage-properties.md).|  
|Propagazione delle modifiche tra gli elementi del modello o tra forme|Vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).|  
|Propagare le modifiche apportate alle risorse, ad esempio altri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni di fuori dell'archivio.|Vedere [gestori propagano le modifiche apportate all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Finestra delle proprietà consente di visualizzare le proprietà di un elemento correlato.|Impostare la proprietà di inoltro. Vedere [personalizzazione della finestra proprietà](../modeling/customizing-the-properties-window.md).|  
|Categorie di proprietà|La finestra proprietà è suddivisa in sezioni denominate le categorie. Impostare il **categoria** delle proprietà di dominio. Proprietà con lo stesso nome di categoria verranno visualizzate nella stessa sezione. È inoltre possibile impostare il **categoria** di un ruolo della relazione.|  
|Controllare l'accesso utente alle proprietà di dominio|Impostare **è esplorabile** false per impedire che una proprietà di dominio visualizzati nella finestra proprietà in fase di esecuzione. È comunque possibile mappare per gli elementi Decorator testo.<br /><br /> **È di sola lettura dell'interfaccia utente** impedisce la modifica di una proprietà di dominio.<br /><br /> Accesso ai programmi per la proprietà di dominio non è interessata.|  
|Modificare il nome, icona e la visibilità dei nodi in Esplora modelli del linguaggio DSL.|Vedere [personalizzazione di Esplora modelli](../modeling/customizing-the-model-explorer.md).|  
|Abilitare la copia, Taglia e Incolla|Impostare il **abilitare Copia Incolla** proprietà del **Editor** nodo in Esplora DSL.|  
|Copiare i relativi obiettivi e i collegamenti di riferimento ogni volta che un elemento viene copiato. Ad esempio, copiare i commenti associati a un elemento.|Impostare il **propaga copia** proprietà del ruolo di origine (rappresentato dalla linea sul lato uno della relazione di dominio nel diagramma DSL Definition).<br /><br /> Scrivere codice per eseguire l'override ProcessOnCopy per ottenere effetti più complessi.<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Eliminare o reimpostato Ricollega elementi correlati quando viene eliminato un elemento.|Impostare il **propaga eliminare** valore di un ruolo della relazione. Per gli effetti più complessi, eseguire l'override `ShouldVisitRelationship` e `ShouldVisitRolePlayer` metodi di `MyDslDeleteClosure` , definita in **DomainModel.cs**<br /><br /> Vedere [personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md)|  
|Mantenere il layout di forma e aspetto nella copia e trascinamento.|Aggiungere le forme e connettori copiato `ElementGroupPrototype`. È il metodo più semplice per eseguire l'override`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Incollare le forme in una posizione prescelta, ad esempio la posizione del cursore attuale.|Eseguire l'override `ClipboardCommandSet.ProcessOnCopy()` per utilizzare la versione del percorso specifica `ElementOperations.Merge().` vedere [personalizzazione copia comportamento](../modeling/customizing-copy-behavior.md).|  
|Creare collegamenti aggiuntivi quando si incolla|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Abilita trascinamento della selezione dal diagramma, altri DSL e Windows elementi|Vedere [procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Consentire una forma o dello strumento è possibile trascinare una forma figlio, ad esempio una porta, come se si sono stato trascinato l'elemento padre.|Definire una direttiva di elemento di tipo Merge per la classe di oggetto di destinazione, per l'inoltro dall'oggetto rilasciato per l'elemento padre. Vedere [personalizzazione la creazione degli elementi e lo spostamento](../modeling/customizing-element-creation-and-movement.md).|  
|Consentire una forma o lo strumento è possibile trascinare una forma e collegamenti aggiuntivi o gli oggetti creati. Ad esempio, per consentire un commento a trascinare un elemento a cui è possibile collegare.|Definire una direttiva di elemento di tipo Merge per la classe di dominio di destinazione e definire i collegamenti da generare. In scenari complessi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione la creazione degli elementi e lo spostamento](../modeling/customizing-element-creation-and-movement.md).|  
|Creare un gruppo di elementi con un unico strumento. Ad esempio, un componente con un set fisso di porte.|Eseguire l'override del metodo di inizializzazione della casella degli strumenti in ToolboxHelper.cs. Creare un elemento gruppo prototipo EGP () che contiene gli elementi e i relativi collegamenti di relazione. Vedere [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Includere le forme dell'entità e la porte nel EGP oppure definire BoundsRules per posizionare le forme porta, quando viene creata un'istanza di EGP. Vedere [BoundsRules vincolare posizione e dimensione](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Utilizzare uno strumento di connessione per creare diversi tipi di relazione.|Aggiungere il generatore di connessione che viene richiamato tramite lo strumento collegamento connettersi direttive LCD (). Il monitor LCD determinare il tipo della relazione tra i tipi di due elementi. Per semplificare questa dipendono gli stati degli elementi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).|  
|Strumenti Sticky - l'utente può fare doppio clic su qualsiasi strumento per creare molte forme o connettori in successione.|In Esplora DSL, selezionare il `Editor` nodo. Nella finestra Proprietà impostare **utilizza permanenti gli elementi della casella degli strumenti**.|  
|Definire i comandi di menu|Vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Vincolare il modello con le regole di convalida|Vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)|  
|Generare codice, i file di configurazione o documenti da un linguaggio DSL.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personalizzare la modalità con cui i modelli vengono salvati in file.|Vedere [personalizzazione di archiviazione di File e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Salvare i modelli di database o altri supporti.|Eseguire l'override *YourLanguage*DocData<br /><br /> Vedere [personalizzazione di archiviazione di File e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrare DSL diversi in modo che funzionino come parte di un'applicazione.|Vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Consentire il modello DSL possono essere estesi da terze parti e l'estensione di controllo.|[Estendere il DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Condivisione di classi tra DSL usando una libreria DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>Vedere anche

[Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
[Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
[SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]