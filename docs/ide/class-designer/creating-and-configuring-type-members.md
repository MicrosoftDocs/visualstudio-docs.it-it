---
title: Creazione e configurazione di membri di tipi (Progettazione classi) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 910860ce3362dd6d87a43df28e0221b404567666
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Creazione e configurazione di membri di tipi (Progettazione classi)
È possibile aggiungere questi membri ai tipi in un diagramma classi e configurarli nella finestra **Dettagli classe**:

|**Type**|**Membri che può contenere**|
|--------------|--------------------------------|
|Classe|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), distruttore (metodo), costante|
|Enum|membro|
|Interfaccia|metodo, proprietà, evento (per C# e Visual Basic)|
|Classe astratta|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), distruttore (metodo), costante|
|Struttura (struct in C#)|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), costante|
|delegato|Parametro|
|Modulo (solo VB)|metodo, proprietà, campo, evento, costruttore, costante|

> [!NOTE]
>  Rendere più concisa la dichiarazione di proprietà se le funzioni di accesso get e set della proprietà non necessitano di logica aggiuntiva mediante proprietà implementate automaticamente (solo C#). Per visualizzare la firma completa, scegliere **Modifica il formato membri**, **Visualizza firma completa** dal menu **Diagramma classi**. Per altre informazioni sulle proprietà implementate automaticamente, vedere [Proprietà implementate automaticamente](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto di supporto|
|----------|------------------------|
|**Introduzione:** prima di creare e configurare membri di tipo, è necessario aprire la finestra Dettagli classe.|-   [Apertura della finestra Dettagli classe](creating-and-configuring-type-members.md#OpenClassDetails)<br />-   [Note sull'uso di Dettagli classe](creating-and-configuring-type-members.md#ClassDetailsUsageNotes)<br />-   [Visualizzare le informazioni di sola lettura](creating-and-configuring-type-members.md#ReadOnlyInfo)<br />-   [Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Creare e modificare membri di tipi:**  è possibile creare nuovi membri, modificare i membri e aggiungere parametri a un metodo tramite la finestra Dettagli classe.|-   [Creazione di membri](creating-and-configuring-type-members.md#CreateMembers)<br />-   [Modifica di membri di tipi](creating-and-configuring-type-members.md#ModifyTypeMembers)<br />-   [Aggiunta di parametri a metodi](creating-and-configuring-type-members.md#AddMethodParams)|

##  <a name="OpenClassDetails"></a> Apertura della finestra Dettagli classe
Per impostazione predefinita, la finestra Dettagli classe viene visualizzata automaticamente quando si apre un nuovo diagramma classi (vedere [Procedura: Aggiungere diagrammi classi ai progetti](how-to-add-class-diagrams-to-projects.md)). È inoltre possibile aprire esplicitamente la finestra Dettagli classe seguendo le istruzioni riportate di seguito.

#### <a name="to-open-the-class-details-window"></a>Per aprire la finestra Dettagli classe

1.  Fare clic con il pulsante destro del mouse su qualsiasi classe nel diagramma per visualizzare un menu di scelta rapida.

2.  Fare clic su **Finestra Dettagli classe** nel menu di scelta rapida.

 - oppure -

-   Scegliere **Altre finestre** dal menu Visualizza e fare clic su **Dettagli classe**.

##  <a name="CreateMembers"></a> Creazione di membri
Per creare un membro, è possibile utilizzare uno dei seguenti strumenti:

-   Progettazione classi

-   Barra degli strumenti della finestra Dettagli classe

-   Finestra Dettagli classe

> [!NOTE]
>  È inoltre possibile creare costruttori e distruttori attenendosi alle procedure descritte in questa sezione. Tenere presente che costruttori e distruttori sono tipi speciali di metodi e, in quanto tali, vengono visualizzatili nel raggruppamento **Metodi** nelle forme del diagramma classi e nella sezione **Metodi** della griglia delle finestra Dettagli classe.

> [!NOTE]
>  L'unica entità che è possibile aggiungere a un delegato è il parametro. Si noti che la procedura "Per creare un membro utilizzando la barra degli strumenti della finestra Dettagli classe" non è valida per questa operazione.

#### <a name="to-create-a-member-using-class-designer"></a>Per creare un membro utilizzando Progettazione classi

1.  Fare clic con il pulsante destro del mouse sul tipo a cui si vuole aggiungere un membro, scegliere **Aggiungi** e scegliere il tipo di membro da aggiungere.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. Il nome predefinito assegnato può essere modificato in **Progettazione classi**, nella finestra **Dettagli classe** oppure nella finestra **Proprietà**.

2.  Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Per creare un membro utilizzando la barra degli strumenti della finestra Dettagli classe

1.  Sulla superficie del diagramma selezionare il tipo a cui aggiungere un membro.

     Il tipo otterrà lo stato attivo e i relativi contenuti verranno visualizzati nella finestra Dettagli classe.

2.  Nella barra degli strumenti della finestra Dettagli classe fare clic sull'icona superiore e scegliere **Nuovo \<membro>** dall'elenco a discesa.

     Il cursore si sposta nel campo **Nome** in una riga per il tipo di membro che si vuole aggiungere. Se, ad esempio, è stata selezionata l'opzione **Nuova proprietà**, il cursore si sposta in una nuova riga nella sezione **Proprietà** della finestra Dettagli classe.

3.  Digitare il nome del membro da creare e premere Invio oppure spostare lo stato attivo in altro modo, ad esempio premendo Tab.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. A questo punto il membro esiste nel codice e viene visualizzato in **Progettazione classi**, nella finestra Dettagli classe e nella finestra Proprietà.

4.  Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

#### <a name="to-create-a-member-using-the-class-details-window"></a>Per creare un membro utilizzando la finestra Dettagli classe

1.  Sulla superficie del diagramma selezionare il tipo a cui aggiungere un membro.

     Il tipo otterrà lo stato attivo e i relativi contenuti verranno visualizzati nella finestra Dettagli classe.

2.  Nella sezione della finestra Dettagli classe che contiene il tipo di membro da aggiungere, scegliere **\<Aggiungi membro>**. Se ad esempio si vuole aggiungere un campo, scegliere **\<Aggiungi campo>**.

3.  Digitare il nome del membro da creare e premere Invio.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. A questo punto il membro esiste nel codice e viene visualizzato in **Progettazione classi**, nella finestra Dettagli classe e nella finestra Proprietà.

4.  Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

     **Nota:** per creare i membri è anche possibile usare i tasti di scelta rapida. Per altre informazioni, vedere [Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

##  <a name="ModifyTypeMembers"></a>Modifica di membri di tipi
Utilizzando Progettazione classi è possibile modificare i membri dei tipi visualizzati nel diagramma. È possibile modificare i membri di qualsiasi tipo visualizzato in un diagramma classi che non sia di sola lettura. È possibile modificare i membri dei tipi utilizzando la modifica sul posto nell'area di progettazione, la finestra Proprietà e la finestra Dettagli classe.

Tutti i membri visualizzati nella finestra Dettagli classe rappresentano i membri dei tipi presenti nel diagramma classi. Sono disponibili quattro tipi di membri: metodi, proprietà, campi ed eventi.

Tutte le righe dei membri sono contraddistinte da intestazioni che raggruppano i membri in base al tipo. Tutte le proprietà vengono ad esempio visualizzate sotto l'intestazione **Proprietà**, che possono essere compresse o espanse come un nodo nella griglia.

Ciascuna riga di membri visualizza i seguenti elementi:

-   **Icona del membro**

     Ciascun tipo di membro è rappresentato dalla rispettiva icona. Posizionare il cursore del mouse sull'icona del membro per visualizzarne la firma. Fare clic sull'icona del membro o sullo spazio vuoto a sinistra per selezionare la riga.

-   **Nome del membro**

     Nella colonna **Nome** della riga di un membro è visualizzato il nome del membro. Questo nome viene visualizzato anche nella proprietà **Nome** nella finestra Proprietà. È possibile utilizzare questa cella per modificare il nome di qualsiasi membro con autorizzazioni di lettura-scrittura.

     Se la colonna **Nome** è troppo stretta per visualizzare l'intero nome, è possibile posizionare il cursore del mouse sul nome del membro per visualizzarlo.

-   **Tipo di membro**

     Nella cella **Tipo di membro** viene usata la tecnologia Intellisense, che consente di scegliere da un elenco di tutti i tipi disponibili nel progetto corrente o nei progetti a cui viene fatto riferimento.

-   **Modificatore del membro**

     È possibile modificare il modificatore di visibilità di un membro in `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`) o `Default`.

-   **\<aggiungi membro>**

     L'ultima riga della finestra Dettagli classe contiene il testo **\<Aggiungi membro>** nella cella **Nome**. Facendo clic su questa cella, è possibile creare un nuovo membro. Per altre informazioni, vedere [Creazione di membri](creating-and-configuring-type-members.md#CreateMembers).

-   **Proprietà dei membri nella finestra Proprietà**

     Nella finestra Dettagli classe viene visualizzato un sottoinsieme delle proprietà dei membri riportate nella finestra Proprietà. La modifica di una proprietà in un percorso aggiorna il valore della proprietà a livello globale. Ciò include la visualizzazione del valore nell'altro percorso.

-   **Riepilogo**

     Nella cella **Riepilogo** è contenuto un riepilogo delle informazioni relative al membro. Fare clic sui puntini di sospensione nella cella **Riepilogo** per visualizzare o modificare le informazioni relative a **Riepilogo**, **Tipo restituito** e **Note** per il membro.

-   **Nascondi**

     Se la casella di controllo **Nascondi** è selezionata, il membro non verrà visualizzato nel tipo.

#### <a name="to-modify-a-type-member"></a>Per modificare un membro di un tipo

1.  Selezionare un tipo utilizzando Progettazione classi.

2.  Se la finestra Dettagli classe non è visualizzata, fare clic sul pulsante **Finestra Dettagli classe** nella barra degli strumenti di Progettazione classi.

3.  Modificare i valori nei campi della griglia della finestra Dettagli classe. Dopo ogni modifica premere INVIO oppure spostare lo stato attivo dal campo modificato, ad esempio premendo TAB. Il codice verrà immediatamente aggiornato in base alle modifiche apportate.

    > [!NOTE]
    >  Se si desidera modificare solo il nome di un membro, è possibile farlo mediante la modifica sul posto.

##  <a name="AddMethodParams"></a> Aggiunta di parametri a metodi
Utilizzare la finestra Dettagli classe per aggiungere parametri ai metodi. I parametri possono essere configurati per essere obbligatori o facoltativi. Se si specifica un valore per la proprietà **Valore predefinito facoltativo** di un parametro, la finestra di progettazione genererà il codice come parametro facoltativo.

Le righe dei parametri contengono i seguenti elementi:

-   **Name**

     La colonna **Nome** di una riga di parametri visualizza il nome del parametro. Questo nome viene visualizzato anche nella proprietà **Nome** nella finestra Proprietà. È possibile utilizzare questa cella per cambiare il nome di qualsiasi parametro con autorizzazioni di lettura-scrittura.

     Se la colonna **Nome** è troppo stretta per visualizzare l'intero nome, è possibile posizionare il cursore del mouse sul nome del parametro per visualizzarlo.

-   **Type**

     Nella cella **Tipo parametro** viene usata la tecnologia IntelliSense, che consente di scegliere da un elenco di tutti i tipi disponibili nel progetto corrente o nei progetti a cui viene fatto riferimento.

-   **Modificatore**

     La cella **Modificatore** di una riga di parametro accetta e visualizza il nuovo modificatore del parametro. Per immettere un nuovo modificatore di parametro, nell'elenco a discesa selezionare **Nessuno**, **ref**, **out** o **params** in C# e **ByVal**, **ByRef** o **ParamArray** in VB.

-   **Riepilogo**

     La cella **Riepilogo** di una riga di parametro consente di immettere i commenti di codice visualizzati in IntelliSense quando si immette il parametro nell'editor di codice.

-   **\<aggiungi parametro>**

     L'ultima riga di parametri di un membro contiene la cella il testo **<add parameter>** nella cella **Nome**. Fare clic in questa cella per creare un nuovo parametro. Per altre informazioni, vedere [Per aggiungere un parametro a un metodo](creating-and-configuring-type-members.md#HowToAddParameterToMethod).

**Proprietà dei parametri nella finestra Proprietà**

Nella finestra Proprietà vengono visualizzate le stesse proprietà dei parametri riportate nella finestra Dettagli classe: **Nome**, **Tipo**, **Modificatore**, **Riepilogo**, nonché la proprietà **Valore predefinito facoltativo**. Se una proprietà viene cambiata in una posizione, il relativo valore verrà aggiornato a livello globale, anche nell'altra posizione.

> [!NOTE]
>  Per aggiungere un parametro a un delegato, vedere [Creazione di membri](creating-and-configuring-type-members.md#CreateMembers).

> [!NOTE]
>  Anche se è un metodo, un distruttore non può avere parametri.

###  <a name="HowToAddParameterToMethod"></a> Per aggiungere un parametro a un metodo

1.  Sulla superficie del diagramma fare clic sul tipo contenente il metodo a cui si desidera aggiungere un parametro.

     Il tipo otterrà lo stato attivo e il relativo contenuto verrà visualizzato nella finestra Dettagli classe.

2.  Nella finestra Dettagli classe espandere la riga del metodo a cui si desidera aggiungere un parametro.

     Viene visualizzata una riga di parametro rientrata, contenente solo una coppia di parentesi e il testo **\<aggiungi parametro>**.

3.  Fare clic su **\<aggiungi parametro>**, digitare il nome del nuovo parametro e premere **INVIO**.

     Il nuovo parametro verrà aggiunto al metodo e al codice del metodo. e verrà visualizzato nelle finestre Dettagli classe e Proprietà.

4.  Se lo si desidera, specificare altri dettagli relativi al parametro, ad esempio il tipo.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Per aggiungere un parametro facoltativo a un metodo

1.  Sulla superficie del diagramma fare clic sul tipo contenente il metodo a cui si desidera aggiungere un parametro facoltativo.

     Il tipo otterrà lo stato attivo e il relativo contenuto verrà visualizzato nella finestra Dettagli classe.

2.  Nella finestra Dettagli classe espandere la riga del metodo a cui si desidera aggiungere un parametro facoltativo.

     Viene visualizzata una riga di parametro rientrata, contenente solo una coppia di parentesi e il testo **\<aggiungi parametro>**.

3.  Fare clic su **\<aggiungi parametro>**, digitare il nome del nuovo parametro e premere **INVIO**.

     Il nuovo parametro verrà aggiunto al metodo e al codice del metodo. e verrà visualizzato nelle finestre Dettagli classe e Proprietà.

4.  Nella finestra Proprietà digitare un valore per la proprietà **Valore predefinito facoltativo**. L'impostazione della proprietà Valore predefinito facoltativo di un parametro lo rende facoltativo.

    > [!NOTE]
    >  I parametri facoltativi devono essere gli ultimi parametri presenti nell'elenco di parametri.

##  <a name="ClassDetailsUsageNotes"></a> Note sull'uso di Dettagli classe
Leggere i suggerimenti riportati di seguito relativi all'utilizzo della finestra Dettagli classe.

**Celle modificabili e non modificabili**

Tutte le celle della finestra Dettagli classe sono modificabili, con alcune eccezioni:

-   L'intero tipo è di sola lettura se, ad esempio, si trova in un assembly a cui viene fatto riferimento. Se si seleziona la forma in Progettazione classi, i relativi dettagli vengono visualizzati in sola lettura nella finestra Dettagli classe.

-   Per gli indicizzatori, il nome è di sola lettura mentre gli altri elementi (tipo, modificatore, riepilogo) sono modificabili.

-   Per tutti i generics sono presenti parametri di sola lettura nella finestra Dettagli classe. Per cambiare tali parametri, è necessario modificare il relativo codice sorgente.

-   Il nome del parametro di tipo definito su un tipo generico è di sola lettura.

-   Se il codice di un tipo è interrotto (non analizzabile), il contenuto del tipo viene visualizzato in sola lettura nella finestra Dettagli classe.

**Finestra Dettagli classe e codice sorgente**

-   Per visualizzare il codice sorgente, fare clic con il pulsante destro del mouse su una forma nella finestra Dettagli classe (o in Progettazione classi) e quindi scegliere Visualizza codice. Il file del codice sorgente verrà aperto e il cursore verrà posizionato sull'elemento selezionato.

-   La visualizzazione di informazioni sulla firma in Progettazione classi e nella finestra Dettagli classe verrà immediatamente aggiornata in base alla modifica del codice sorgente. Se la finestra Dettagli classe è chiusa, le nuove informazioni saranno visibili alla successiva apertura.

-   Se il codice di un tipo è interrotto (non analizzabile), il contenuto del tipo verrà visualizzato in sola lettura nella finestra Dettagli classe.

**Funzionalità Appunti nella finestra Dettagli classe**

 È possibile copiare o tagliare campi o righe dalla finestra Dettagli classe e incollarli in un altro tipo. Le righe possono essere tagliate solo se non sono di sola lettura. Quando una riga viene incollata, la finestra Dettagli classe assegna un nuovo nome (derivato dal nome della riga copiata) per evitare conflitti.

##  <a name="ReadOnlyInfo"></a> Visualizzare le informazioni di sola lettura
In Progettazione classi e nella finestra Dettagli classe è possibile visualizzare i tipi (e i membri dei tipi) per i seguenti elementi:

-   un progetto contenente un diagramma classi;

-   un progetto a cui viene fatto riferimento da un progetto contenente un diagramma classi;

-   un assembly a cui viene fatto riferimento da un progetto contenente un diagramma classi.

Negli ultimi due casi, l'entità a cui viene fatto riferimento (un tipo o un membro) è in sola lettura nel diagramma classi che la rappresenta.

Un intero progetto o parti di esso, ad esempio singoli file, possono essere in sola lettura. Nella maggior parte dei casi un progetto o uno dei relativi file è in sola lettura quando è incluso nel controllo del codice sorgente (e non estratto), esiste in un assembly esterno oppure il sistema operativo considera i file in sola lettura.

**Controllo del codice sorgente**

Poiché un diagramma classi viene salvato come file in un progetto, è necessario estrarre il progetto per salvare tutte le modifiche apportate in Progettazione classi o nella finestra Dettagli classe.

**Progetti di sola lettura**

Il progetto può essere in sola lettura per un motivo diverso dal controllo del codice sorgente. Se si chiude il progetto verrà visualizzata una finestra di dialogo in cui viene chiesto se si vuole sovrascrivere il file del progetto, ignorare le modifiche (non salvarle) o annullare l'operazione di chiusura. Se si sceglie di sovrascrivere, i file del progetto verranno sovrascritti e diventeranno di lettura-scrittura. Verrà inoltre aggiunto il nuovo file del diagramma classi.

**Tipi di sola lettura**

Se si prova a salvare un progetto contenente un tipo il cui file del codice sorgente è di sola lettura, verrà visualizzata la finestra di dialogo **Salvataggio file in sola lettura**, in cui sono disponibili le opzioni per salvare il file con un nuovo nome o in un nuovo percorso oppure per sovrascrivere il file di sola lettura. Se si sceglie di sovrascrivere il file, la nuova copia non sarà più in sola lettura.

Se un file di codice contiene un errore di sintassi, le forme che visualizzano il codice in quel file saranno temporaneamente in sola lettura finché l'errore di sintassi non viene corretto. Le forme in questo stato sono caratterizzate da testo di colore rosso e da un'icona rossa con una descrizione che indica un errore di analisi nel file del codice sorgente.

Un tipo a cui viene fatto riferimento (ad esempio un tipo .NET Framework), che esiste all'interno di un altro nodo di progetto o di un nodo di assembly a cui viene fatto riferimento, nell'area di progettazione di Progettazione classi viene indicato come in sola lettura. Un tipo locale, che esiste nel progetto aperto, è in lettura-scrittura e la relativa forma viene indicata come tale nell'area di progettazione di Progettazione classi.

Gli indicizzatori sono in lettura-scrittura nel codice e nella finestra Dettagli classe, ma il nome dell'indicizzatore è in sola lettura.

I metodi parziali non possono essere modificati mediante Progettazione classi o la finestra Dettagli classe ma devono essere modificati con l'editor del codice.

Il codice C++ nativo non può essere modificato mediante Progettazione classi o la finestra Dettagli classe ma deve essere modificato con l'editor del codice.

## <a name="see-also"></a>Vedere anche

- [Visualizzazione di tipi e relazioni](viewing-types-and-relationships.md)
- [Refactoring di classi e tipi](refactoring-classes-and-types.md)