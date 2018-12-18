---
title: IntelliSense per C# | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1a443258d7f3b71c8f14cb967fc37090f80b5ad5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="c-intellisense"></a>IntelliSense per C#

IntelliSense per C# è disponibile durante la scrittura del codice nell'editor e durante il debug nella finestra di comando [Modalità immediata](../ide/reference/immediate-window.md).

## <a name="completion-lists"></a>Elenchi di completamento

Gli elenchi di completamento di IntelliSense in C# contengono token di Elenca membri, Completa parola e altri ancora. Forniscono funzionalità di accesso rapido a:

- Membri di un tipo o spazio dei nomi

- Nomi di variabili, comandi e funzioni

- Frammenti di codice

- Parole chiave del linguaggio

- Metodi di estensione

L’Elenco di completamento in C# può escludere i token irrilevanti e preselezionare quelli pertinenti al contesto. Per altre informazioni, vedere [Elenchi di completamento filtrati](#filtered-completion-lists).

## <a name="code-snippets-in-completion-lists"></a>Frammenti di codice negli elenchi di completamento

In C#, l'elenco di completamento include frammenti di codice che consentono di inserire facilmente corpi predefiniti di codice nel programma. I frammenti di codice vengono visualizzati nell'elenco di completamento come [testo del collegamento](../ide/code-snippets-schema-reference.md#shortcut) del frammento di codice. Per altre informazioni sui frammenti di codice disponibili per impostazione predefinita in C#, vedere [Frammenti di codice C#](../ide/visual-csharp-code-snippets.md).

## <a name="language-keywords-in-completion-lists"></a>Parole chiave del linguaggio negli elenchi di completamento

In C#, l'elenco di completamento include anche le parole chiave del linguaggio. Per altre informazioni sulle parole chiave del linguaggio C#, vedere [Parole chiave di C#](/dotnet/csharp/language-reference/keywords/index).

## <a name="extension-methods-in-completion-lists"></a>Metodi Estensione negli elenchi di completamento

In C#, l'elenco di completamento include i metodi estensione che rientrano nell'ambito.

> [!NOTE]
> Nell'elenco di completamento non vengono visualizzati tutti i metodi di estensione degli oggetti <xref:System.String>.

I metodi di estensione usano un'icona diversa rispetto ai metodi di istanza. Per un elenco di icone dell’elenco, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). Se un metodo di istanza e un metodo di estensione con lo stesso nome sono entrambi inclusi in un ambito, nell'elenco di completamento viene visualizzata l'icona del metodo di estensione.

## <a name="filtered-completion-lists"></a>Elenchi di completamento filtrati

I membri non necessari vengono rimossi dall'elenco di completamento IntelliSense usando dei filtri. In C# vengono filtrati gli elenchi di completamento disponibili per le voci riportate di seguito:

- **Interfacce e classi di base**: IntelliSense rimuove automaticamente le voci dagli elenchi di completamento per interfacce e classi base, sia negli elenchi di interfacce e di dichiarazioni di classe base sia negli elenchi di vincoli. Le enumerazioni, ad esempio, non vengono visualizzate nell'elenco di completamento delle classi base perché non possono essere usate per tali classi. L'elenco di completamento delle classi base contiene solo interfacce e spazi dei nomi. Se si seleziona una voce nell'elenco e si digita una virgola, IntelliSense rimuove le classi di base dall'elenco di completamento perché C# non supporta l'ereditarietà multipla. Lo stesso comportamento si verifica anche per le clausole di vincoli.

- **Attributi**: quando si applica un attributo a un tipo, l'elenco di completamento viene filtrato in modo da contenere solo i tipi che discendono dagli spazi dei nomi contenenti tali tipi, ad esempio <xref:System.Attribute>.

- **Clausole catch**

- **Inizializzatori di oggetto**: solo i membri che possono essere inizializzati verranno visualizzati nell'elenco di completamento.

- **Nuova parola chiave**: quando si digita `new` e si preme la BARRA SPAZIATRICE, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Per le dichiarazioni e per le istruzioni return nei metodi, ad esempio, vengono selezionate automaticamente delle voci nell'elenco di completamento.

- **Parola chiave enum**: quando si preme la BARRA SPAZIATRICE dopo il segno di uguale per un'assegnazione enum, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Dopo aver digitato la parola chiave return e quando si crea una dichiarazione, ad esempio, le voci nell'elenco di completamento vengono selezionate automaticamente.

- **Operatori as e is**: quando si preme la BARRA SPAZIATRICE dopo aver digitato la parola chiave `as` o `is` viene visualizzato automaticamente un elenco di completamento filtrato.

- **Eventi**: quando si digita la parola chiave `event` l'elenco di completamento contiene solo tipi delegati.

- Il **parametro help** consente di ordinare automaticamente il primo overload di metodo corrispondente ai parametri immessi. Se sono disponibili più overload di metodi, è possibile usare le frecce verso l'alto e verso il basso per selezionare il successivo overload possibile in elenco.

## <a name="most-recently-used-members"></a>Membri utilizzati più di recente

IntelliSense memorizza i membri recentemente selezionati nella casella popup [Elenca membri](../ide/using-intellisense.md) per il completamento del nome oggetto automatico. La volta successiva che si utilizza l'elenco dei membri, i membri utilizzati di recente vengono visualizzati nella parte superiore. La cronologia dei membri utilizzati più di recente viene cancellata tra ogni sessione nell'ambiente di sviluppo integrato.

## <a name="override"></a>override

Quando si digita [override](/dotnet/csharp/language-reference/keywords/override) e si preme BARRA SPAZIATRICE, IntelliSense visualizza in una casella di riepilogo popup tutti i membri validi della classe di base di cui è possibile eseguire l'override. Digitando il tipo restituito del metodo dopo `override`, IntelliSense visualizzerà soltanto i metodi che restituiscono lo stesso tipo. Se non vengono trovate corrispondenze, IntelliSense visualizzerà tutti i membri della classe base.

## <a name="automatic-code-generation"></a>Generazione automatica di codice

### <a name="add-using"></a>Aggiungi using

L'operazione **Aggiungi using** di IntelliSense aggiunge automaticamente la direttiva `using` richiesta al file di codice. Questa funzione consente di restare concentrati sul codice che si sta scrivendo anziché passare a un'altra parte del codice.

Per avviare l'operazione di aggiunta della direttiva using, posizionare il cursore sul riferimento a un tipo che non può essere risolto. Ad esempio, quando si crea un'applicazione console e si aggiunge `XmlTextReader` al corpo del metodo `Main`, nella riga di codice appare una sottolineatura ondulata rossa per indicare che non è possibile risolvere il riferimento al tipo. È quindi possibile richiamare Aggiungi using con l'azione rapida. L'azione rapida viene visualizzata solo quando il cursore è posizionato sul tipo non associato.

![Immagine ampliata Aggiungi using, azione rapida](../ide/media/addusing-quickaction.png "AddUsing-QuickAction")

Fare clic sull'icona lampadina e quindi scegliere **using System.Xml;** per aggiungere automaticamente la direttiva using.

### <a name="remove-and-sort-usings"></a>Opzione Rimuovi e ordina using

L'opzione **Rimuovi e ordina using** consente di ordinare e rimuovere le dichiarazioni `using` e `extern` senza modificare il comportamento del codice sorgente. Nel tempo i file di origine possono diventare troppo grandi e difficili da leggere a causa di direttive `using` superflue e non organizzate. L'opzione **Rimuovi e ordina using** compatta il codice sorgente rimuovendo le direttive `using` inutilizzate e migliora la leggibilità mettendole in ordine. Dal menu **Modifica** scegliere **IntelliSense** e **Organizza using**.

### <a name="implement-interface"></a>Implementa interfaccia

IntelliSense offre un'opzione che consente di implementare un'[interfaccia](/dotnet/csharp/language-reference/keywords/interface) mentre si usa l'editor di codice. Per implementare correttamente un'interfaccia è in genere necessario creare una dichiarazione di metodo per ogni membro dell'interfaccia della classe. Usando IntelliSense, dopo aver digitato il nome di un'interfaccia in una dichiarazione di classe viene visualizzata la lampadina delle Azioni rapide. La lampadina offre la possibilità di implementare automaticamente l'interfaccia, usando la denominazione esplicita o implicita. Con la denominazione esplicita, le dichiarazioni di metodo contengono il nome dell'interfaccia. Con la denominazione implicita, le dichiarazioni di metodo non indicano l'interfaccia a cui appartengono. Un metodo di interfaccia con denominazione esplicita è accessibile solo tramite un'istanza di interfaccia e non tramite un'istanza di classe. Per altre informazioni, vedere [Implementazione esplicita dell'interfaccia](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Con Implementa interfaccia verrà generato il numero minimo di stub di metodo necessario per soddisfare l'interfaccia. Se una classe base implementa parti dell'interfaccia, tali stub non verranno rigenerati.

### <a name="implement-abstract-base-class"></a>Implementare una classe di base astratta

IntelliSense offre un'opzione che consente di implementare automaticamente i membri di una classe base astratta mentre si usa l'editor di codice. Per implementare i membri di una classe base astratta è in genere necessario creare una nuova definizione di metodo per ciascun metodo della classe base astratta nella classe derivata. Con IntelliSense, dopo aver digitato il nome di una classe di base astratta in una dichiarazione di classe viene visualizzata la lampadina delle Azioni rapide. La lampadina offre la possibilità di implementare automaticamente i metodi della classe di base.

Gli stub di metodo generati con la funzionalità di implementazione di una classe base astratta vengono modellati in base al frammento di codice definito nel file MethodStub.snippet. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generazione dall'utilizzo

La funzionalità di **generazione dall'utilizzo** consente di usare le classi e i membri prima di definirli. È possibile generare uno stub per qualsiasi classe, costruttore, metodo, proprietà, campo o enumerazione che si desidera utilizzare, ma che non è ancora stato definito. È possibile generare nuovi tipi e membri senza abbandonare la posizione corrente nel codice. Ciò riduce al minimo l'interruzione del flusso di lavoro.

Viene visualizzata una sottolineatura ondulata rossa sotto ogni identificatore non definito. Quando si posiziona il puntatore del mouse sull'identificatore, viene visualizzato un messaggio di errore in una descrizione comando. Per visualizzare le opzioni appropriate, è possibile utilizzare le procedure seguenti:

- Fare clic sull'identificatore non definito. Viene visualizzata la lampadina delle Azioni rapide sotto l'identificatore. Fare clic sulla lampadina.

- Fare clic sull'identificatore non definito e premere **CTRL** + **.** (CTRL + punto).

- Fare clic con il pulsante destro del mouse sull'identificatore non definito e quindi scegliere **Azioni rapide e refactoring**.

Le opzioni visualizzate possono includere quanto segue:

- **Genera proprietà**

- **Genera campo**

- **Genera metodo**

- **Genera classe**

- **Genera nuovo tipo** (per una classe, struct, interfaccia o enumerazione)

## <a name="generate-event-handlers"></a>Genera gestori eventi

Nell'editor del codice, IntelliSense consente di agganciare i metodi (gestori eventi) ai campi evento.

Quando si digita l'operatore `+=` dopo un campo evento in un file con estensione cs, IntelliSense chiede di premere **TAB**. Questa operazione consente di inserire una nuova istanza di un delegato che punta al metodo che gestisce l'evento.

![Associazione automatica dei pulsanti](../ide/media/vxautohookup.gif "vxAutoHookUp")

Se si preme **TAB**, IntelliSense termina automaticamente l'istruzione per l'utente e visualizza il riferimento al gestore dell'evento come testo selezionato nell'editor del codice. Per completare l'associazione automatica dell'evento, IntelliSense chiede di premere di nuovo **TAB** per creare uno stub vuoto per il gestore dell'evento.

![Genera gestore eventi](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")

> [!NOTE]
> Se un nuovo delegato creato da IntelliSense fa riferimento a un gestore eventi esistente, IntelliSense comunica queste informazioni nella descrizione comando. È quindi possibile modificare questo riferimento. Il testo è già selezionato nell'editor del codice. In caso contrario, l'associazione automatica dell'evento è a questo punto completata.

Se si preme **TAB**, IntelliSense associa automaticamente un metodo con la firma corretta e posiziona il cursore nel corpo del gestore dell'evento.

> [!NOTE]
> Usare il comando **Posizione precedente** nel menu **Visualizza** (**CTRL** + **-**) per tornare all'istruzione di associazione dell'evento.

## <a name="see-also"></a>Vedere anche

[Utilizzo di IntelliSense](../ide/using-intellisense.md)  
[IDE di Visual Studio](../ide/visual-studio-ide.md)