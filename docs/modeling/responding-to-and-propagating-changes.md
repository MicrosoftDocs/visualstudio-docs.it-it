---
title: La propagazione delle modifiche e rispondere ai | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f814cc9ca963b59217dc486539d22f42f487a3db
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="responding-to-and-propagating-changes"></a>Risposta alle modifiche e propagazione delle modifiche
Quando un elemento viene creato, eliminato o aggiornato, è possibile scrivere codice che propaga le modifiche ad altre parti del modello o a risorse esterne, ad esempio file, database o altri componenti.  
  
## <a name="in-this-section"></a>In questa sezione  
 Come indicazione generale, prendere in considerazione queste tecniche nell'ordine seguente:  
  
|Tecnica|Scenari|Per altre informazioni|  
|---------------|---------------|--------------------------|  
|Definire una proprietà dominio calcolato.|Una proprietà di dominio il cui valore viene calcolato da altre proprietà nel modello. Ad esempio, un prezzo è la somma dei prezzi di elementi correlati.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|  
|Definire una proprietà di dominio di archiviazione personalizzato.|Proprietà dominio archiviate in altre parti del modello o esternamente. Ad esempio, è stato possibile analizzare una stringa di espressione in una struttura ad albero del modello.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|  
|Eseguire l'override dei gestori di modifica, ad esempio OnValueChanging e OnDeleting|Mantenere sincronizzati i diversi elementi e mantenere i valori esterni sincronizzato con il modello.<br /><br /> Vincolare i valori per intervalli definiti.<br /><br /> Chiamato immediatamente prima e dopo il valore della proprietà e altre modifiche. Per terminare la modifica, è possibile generare un'eccezione.|[Gestori di modifica del valore delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md)|  
|Regole|È possibile definire regole che vengono messe in coda per l'esecuzione appena prima della fine di una transazione in cui si è verificata una modifica. Questi non vengono eseguiti su annullamento o ripetizione. Utilizzarle per garantire la sincronizzazione con un'altra parte dell'archivio.|[Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md)|  
|Eventi di archiviazione|L'archivio di modellazione fornisce notifiche di eventi, ad esempio aggiunta o eliminazione di un elemento o un collegamento o la modifica del valore di una proprietà. L'evento viene eseguito anche su Annulla e Ripeti. Utilizzare gli eventi di archiviazione per aggiornare i valori che non sono presenti nell'archivio.|[I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Eventi di .NET|Forme dispongono di gestori di eventi che rispondono a clic del mouse e altre combinazioni. È necessario registrare per questi eventi per ogni oggetto. La registrazione in genere viene eseguita in un override di InitializeInstanceResources e deve essere eseguita per ogni elemento.<br /><br /> Questi eventi si verificano in genere all'esterno di una transazione.|[Procedura: Intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Regole di limiti|Una regola di limiti viene utilizzata in particolare per vincolare i limiti di una forma.|[Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Regole di selezione|Le regole di selezione in modo specifico vincolano ciò che è possibile selezionare l'utente.|[Procedura: Accedere e vincolare la selezione corrente](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Indicare gli stati degli elementi del modello utilizzando le funzionalità di forme e connettori, ad esempio shadow, frecce, colore e larghezza delle linee e lo stile.|[Aggiornamento di forme e di connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Le regole di confrontare e gli eventi di archiviazione**  
 Modifica notificanti, regole e gli eventi vengono eseguiti quando vengono apportate in un modello.  
  
 Le regole vengono in genere applicate alla transazione end in cui si è verificata la modifica e gli eventi vengono applicati dopo il commit delle modifiche in una transazione.  
  
 Utilizzare gli eventi di archiviazione per sincronizzare il modello con gli oggetti di fuori di archivio e le regole per mantenere la coerenza all'interno dell'archivio.  
  
-   **Creazione di regole personalizzate** si crea una regola personalizzata come una classe derivata da una regola astratta. È anche necessario notificare il framework sulla regola personalizzata. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **La sottoscrizione di eventi** prima di è possibile sottoscrivere un evento, creare un gestore dell'evento e delegato. Utilizzare quindi la <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>proprietà per sottoscrivere l'evento. Per ulteriori informazioni, vedere [gestori propagare le modifiche di fuori di modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Annullamento delle modifiche** quando si annulla una transazione, vengono generati eventi, ma non vengono applicate le regole. Se una regola di modifica di un valore e si annulla la modifica, il valore viene reimpostato il valore originale durante l'operazione di annullamento. Quando viene generato un evento, è necessario modificare manualmente il valore al valore originale. Per ulteriori informazioni sulla transactons e di annullamento, vedere [procedura: utilizzare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Il passaggio di argomenti dell'evento a regole e gli eventi** entrambi gli eventi e le regole vengono passate un `EventArgs` parametro che contiene informazioni su come il modello modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)