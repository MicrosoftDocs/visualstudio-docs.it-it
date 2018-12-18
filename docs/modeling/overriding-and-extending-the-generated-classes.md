---
title: Si esegue l'override ed estendere le classi generate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f86600b6fd4bb272ece4454e9a94032ed05f3af1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>Override ed estensione delle classi generate
La definizione DSL è una piattaforma in cui è possibile compilare un potente set di strumenti che dipendono da un linguaggio specifico di dominio. Eseguendo l'override e di estendere le classi generate dalla definizione del linguaggio DSL è possono eseguire molte estensioni e gli adeguamenti. Tali classi includono non solo le classi di dominio che è stato definito in modo esplicito nel diagramma della definizione DSL, ma anche altre classi che definiscono la casella degli strumenti, Esplora, la serializzazione e così via.  
  
## <a name="extensibility-mechanisms"></a>Meccanismi di estendibilità  
 Per consentire di estendere il codice generato sono disponibili diversi meccanismi.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Metodi di override in una classe parziale  
 Le definizioni di classe parziale consentono una classe di essere definito in più posizioni. In questo modo è possibile separare il codice generato da codice scritto personalmente. Nel codice scritto manualmente, è possibile sostituire le classi ereditate dal codice generato.  
  
 Ad esempio, se nella propria definizione DSL si definisce una classe di dominio denominata `Book`, è possibile scrivere codice personalizzato che aggiunge metodi di override:  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Per eseguire l'override di metodi in una classe generata, scrivere sempre il codice in un file che è separato dal file generati. In genere, il file è contenuto in una cartella denominata CustomCode. Se si apportano modifiche al codice generato, andranno persi quando si rigenera il codice dalla definizione del linguaggio DSL.  
  
 Per individuare i metodi è possibile eseguire l'override, digitare **override** nella classe, seguito da uno spazio. La descrizione comando IntelliSense indicherà quali metodi possono essere ignorati.  
  
### <a name="double-derived-classes"></a>Classi derivate da Double  
 La maggior parte dei metodi nelle classi generate vengono ereditata da un set predefinito di classi negli spazi dei nomi di modellazione. Tuttavia, alcuni metodi sono definiti nel codice generato. In genere, ciò significa che è possibile eseguire l'override. è possibile eseguire l'override in una classe parziale i metodi definiti in un'altra definizione parziale della stessa classe.  
  
 Tuttavia, è possibile eseguire l'override di questi metodi impostando il **genera derivato doppie** flag per la classe di dominio. Questo causa due classi da generare, uno da una classe base astratta di altro. Tutte le definizioni di metodo e proprietà sono nella classe base e solo il costruttore è nella classe derivata.  
  
 Ad esempio, nell'esempio Library.dsl, il `CirculationBook` classe di dominio ha il `Generates``Double Derived` proprietà impostata su `true`. Il codice generato per tale classe di dominio contiene due classi:  
  
-   `CirculationBookBase`, che è una classe astratta e che contiene tutti i metodi e proprietà.  
  
-   `CirculationBook`, che deriva da `CirculationBookBase`. È vuoto, ad eccezione di costruttori.  
  
 Per eseguire l'override di qualsiasi metodo, si crea una definizione parziale della classe derivata, ad esempio `CirculationBook`. È possibile eseguire l'override di entrambi i metodi ereditati da framework di modellazione e i metodi generati.  
  
 È possibile utilizzare questo metodo con tutti i tipi di elemento, inclusi i connettori, relazioni, forme, diagrammi e gli elementi del modello. È anche possibile eseguire l'override di metodi di altre classi generate. Alcune classi vengono generate, ad esempio il ToolboxHelper sono sempre derivato doppia.  
  
### <a name="custom-constructors"></a>Costruttori personalizzati  
 È possibile eseguire l'override di un costruttore. Anche nelle classi derivate doppia, deve essere il costruttore nella classe derivata.  
  
 Se si desidera fornire un costruttore personalizzato, è possibile farlo impostando `Has Custom Constructor` per la classe di dominio nella definizione del linguaggio DSL. Quando fa clic su **Trasforma tutti i modelli**, il codice generato non include un costruttore per tale classe. Esso include una chiamata al costruttore manca. In questo modo una segnalazione di errore quando si compila la soluzione. Fare doppio clic sulla segnalazione errori per visualizzare un commento nel codice generato che spiega cosa è necessario fornire.  
  
 Scrivere una definizione di classe parziale in un file separato dal file generati e fornire il costruttore.  
  
### <a name="flagged-extension-points"></a>Punti di estensione con flag  
 Un punto di estensione con flag è una posizione nella definizione del linguaggio specifico di dominio in cui è possibile impostare una proprietà o una casella di controllo per indicare che verrà fornito un metodo personalizzato. Costruttori personalizzati sono un esempio. Altri esempi includono l'impostazione di `Kind` di una proprietà dominio calcolato o archiviazione personalizzata o impostazione di **personalizzato è** flag in un generatore di connessione.  
  
 In ogni caso, quando si imposta il flag e rigenerare il codice, verrà generato un errore di compilazione. Fare doppio clic per visualizzare un commento che spiega che cos'è necessario fornire l'errore.  
  
### <a name="rules"></a>Regole  
 Il gestore delle transazioni consente di definire regole da eseguire prima della fine di una transazione in cui designato verificato un evento, ad esempio una modifica in una proprietà. Le regole vengono in genere utilizzate per mantenere synchronism tra diversi elementi nell'archivio. Ad esempio, le regole vengono utilizzate per assicurarsi che il diagramma consente di visualizzare lo stato corrente del modello.  
  
 Le regole vengono definite per ogni classe, in modo che non si dispone di codice che registra la regola per ogni oggetto. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Eventi di archiviazione  
 L'archivio di modellazione fornisce un meccanismo degli eventi che è possibile utilizzare per l'ascolto per tipi specifici di modifica nell'archivio, tra cui l'aggiunta e l'eliminazione di elementi, le modifiche ai valori delle proprietà e così via. I gestori eventi vengono chiamati dopo la chiusura della transazione in cui sono state apportate le modifiche. In genere, questi eventi vengono utilizzati per aggiornare le risorse all'esterno dell'archivio.  
  
### <a name="net-events"></a>Eventi di .NET  
 È possibile sottoscrivere alcuni eventi delle forme. Ad esempio, può restare in ascolto per il clic del mouse su una forma. È necessario scrivere codice che sottoscrive l'evento per ogni oggetto. Questo codice può essere scritto in un override di InitializeInstanceResources().  
  
 Alcuni eventi vengono generati ShapeFields, utilizzato per disegnare gli elementi Decorator su una forma. Per un esempio, vedere [procedura: intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 In genere non si verificano tali eventi all'interno di una transazione. Se si desidera apportare modifiche nell'archivio, è necessario creare una transazione.