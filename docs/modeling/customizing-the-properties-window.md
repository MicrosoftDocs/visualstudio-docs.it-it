---
title: Personalizzazione della finestra Proprietà
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 50753da026f091d541bffd664f0aa964b4cba3f0
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-the-properties-window"></a>Personalizzazione della finestra Proprietà
È possibile personalizzare l'aspetto e il comportamento della finestra proprietà nel linguaggio specifico di dominio (DSL) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nella definizione DSL, definire le proprietà del dominio su ogni classe di dominio. Per impostazione predefinita, quando si seleziona un'istanza della classe, in un diagramma o in Esplora modelli, ogni proprietà del dominio è elencato nella finestra Proprietà. Questo consente di visualizzare e modificare i valori delle proprietà di dominio, anche se non li mappata a campi di forma nel diagramma.

## <a name="names-descriptions-and-categories"></a>I nomi, descrizioni e le categorie
 **Nome e il nome visualizzato**. Nella definizione di una proprietà di dominio, il nome visualizzato della proprietà è il nome visualizzato in fase di esecuzione nella finestra Proprietà. Al contrario, il nome viene utilizzato quando si scrive codice di programma per aggiornare la proprietà. Il nome deve essere un nome alfanumerico CLR corretto, ma il nome può contenere spazi.

 Quando si imposta il nome di una proprietà nella definizione del linguaggio DSL, il nome visualizzato è automaticamente impostato su una copia del nome. Se si scrive un nome di maiuscole e minuscole Pascal, ad esempio "FuelGauge", il nome visualizzato conterrà automaticamente uno spazio: "Carburante misuratore". Tuttavia, è possibile impostare il nome visualizzato in modo esplicito a un altro valore.

 **Descrizione**. La descrizione di una proprietà di dominio viene visualizzato in due posizioni:

-   Nella parte inferiore della finestra Proprietà quando l'utente seleziona la proprietà. È possibile utilizzare, per indicare all'utente la proprietà rappresenta.

-   Nel codice programma generato. Se si utilizzano le funzionalità per la documentazione per estrarre la documentazione dell'API, viene visualizzato come descrizione di questa proprietà nell'API.

 **Categoria**. Una categoria è un titolo nella finestra Proprietà.

## <a name="exposing-style-features"></a>Esposizione di funzionalità di stile
 Alcune delle funzionalità dinamica di elementi grafici possono essere rappresentati o *esposti* come proprietà di dominio. Una funzionalità che è stato esposto in questo modo può essere aggiornata dall'utente e più facilmente aggiornabili da codice programma.

 Fare doppio clic su una classe di forma nella definizione DSL, scegliere **aggiungere esposti**, quindi scegliere una funzionalità.

 Sulle forme è possibile esporre il **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** e **FillGradientMode** proprietà. I connettori, è possibile esporre il **colore**`,`**TextColor**, **DashStyle**, e **spessore** proprietà. Nei diagrammi è possibile esporre il **FillColor** e **TextColor** proprietà.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Inoltro: Visualizzazione delle proprietà di elementi correlati
 Quando l'utente di tale linguaggio DSL seleziona un elemento in un modello, le proprietà dell'elemento vengono visualizzate nella finestra Proprietà. Tuttavia, è inoltre possibile visualizzare le proprietà di elementi correlati specificati. Ciò è utile se è stato definito un gruppo di elementi che funziona insieme. Ad esempio, è possibile definire un elemento principale e un elemento facoltativo del plug-in. Se l'elemento principale viene eseguito il mapping a una forma e l'altro non lo è, è utile visualizzare tutte le relative proprietà, come se fossero per un solo elemento.

 Questo effetto è denominato *inoltro proprietà*, e viene eseguito automaticamente in molti casi. In altri casi, è possibile ottenere proprietà inoltro definendo un descrittore di tipo di dominio.

### <a name="default-property-forwarding-cases"></a>Casi di inoltro di proprietà predefiniti
 Quando l'utente seleziona una forma o connettore o da un elemento in Esplora risorse, le proprietà seguenti vengono visualizzate nella finestra Proprietà:

-   Proprietà del dominio che sono definite nella classe di dominio dell'elemento del modello, inclusi quelli che sono definiti nelle classi di base. Un'eccezione è una proprietà di dominio per cui sono stati impostati **è esplorabile** a `False`.

-   I nomi degli elementi collegati tramite relazioni che dispongono di una molteplicità di 0..1. Fornisce un metodo comodo per visualizzare facoltativamente collegati a elementi, anche se non è stato definito un mapping di connettore per la relazione.

-   Proprietà di dominio della relazione di incorporamento destinato l'elemento. Perché le relazioni di incorporamento in genere non vengono visualizzate in modo esplicito, questo consente all'utente di vedere le relative proprietà.

-   Proprietà di dominio vengono definite per la forma selezionata o il connettore.

### <a name="adding-property-forwarding"></a>Aggiunta di proprietà inoltro
 Per l'inoltro di una proprietà, definire un descrittore di tipo di dominio. Se si dispone di una relazione di dominio tra due classi di dominio, è possibile utilizzare un descrittore di tipo di dominio per impostare una proprietà di dominio nella prima classe per il valore di una proprietà di dominio nella seconda classe di dominio. Ad esempio, se si dispone di una relazione tra un **Book** classe di dominio e un **autore** classe di dominio, è possibile utilizzare un descrittore di tipo di dominio per rendere il **nome** proprietà di un Libro **autore** vengono visualizzati nella finestra Proprietà quando l'utente seleziona il libro.

> [!NOTE]
>  Inoltro proprietà interessa solo la finestra Proprietà quando l'utente sta modificando un modello. Definisce una proprietà di dominio non nella classe del ricevente. Se si desidera accedere alla proprietà dominio inoltrati in altre parti della definizione DSL o nel codice programma, è necessario accedere all'elemento di inoltro.

 La procedura seguente si presuppone che sia stato creato un linguaggio DSL. I primi passaggi riepilogano i prerequisiti.

##### <a name="to-forward-a-property-from-another-element"></a>Per l'inoltro di una proprietà da un altro elemento

1.  Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione che contiene almeno due classi, che in questo esempio vengono chiamate **Book** e **autore**. Deve esistere una relazione di entrambi i tipi tra **Book** e **autore**.

     La molteplicità del ruolo di origine (il ruolo di **libro** lato) deve essere 1 o 1, 0..1 in modo che ogni **libro** dispone di uno **autore**.

2.  In **Esplora DSL**, fare doppio clic su di **Book** classe di dominio e quindi fare clic su **aggiungere nuovo DomainTypeDescriptor**.

     Un nodo denominato **percorsi di descrittori di proprietà personalizzato** viene visualizzata sotto il **descrittore di tipo personalizzato** nodo.

3.  Fare doppio clic su di **descrittore di tipo personalizzato** nodo e quindi fare clic su **aggiungere nuovo PropertyPath**.

     Un nuovo percorso della proprietà viene visualizzata sotto il **percorsi di descrittori di proprietà personalizzato** nodo.

4.  Selezionare il nuovo percorso di proprietà e il **proprietà** finestra, impostare **percorso per la proprietà** al percorso dell'elemento del modello appropriato.

     Facendo clic sulla freccia rivolta verso il basso a destra di questa proprietà, è possibile modificare il percorso in una visualizzazione albero. Per ulteriori informazioni sui percorsi di dominio, vedere [sintassi del percorso di dominio](../modeling/domain-path-syntax.md). Quando è stato modificato, il percorso dovrebbe essere simile **BookReferencesAuthor.Author/! Autore**.

5.  Impostare **proprietà** per il **nome** proprietà dominio di **autore**.

6.  Impostare **nome visualizzato** a **creare nome**.

7.  Trasforma tutti i modelli, compilare ed eseguire del linguaggio DSL.

8.  In un diagramma del modello, creare un libro, un autore e collegarle utilizzando la relazione di riferimento. Selezionare l'elemento "book" e nella finestra proprietà si dovrebbe essere il nome dell'autore oltre alle proprietà del libro. Modificare il nome dell'autore, collegato o collegare il libro da un altro autore e osservare che il nome dell'autore del libro è stato modificato.

## <a name="custom-property-editors"></a>Editor di proprietà personalizzati
 Finestra delle proprietà fornisce un valore predefinito appropriato strumento di modifica per il tipo di ogni proprietà del dominio. Ad esempio, per un tipo enumerato, l'utente visualizza un elenco a discesa e per una proprietà numerica, l'utente può immettere cifre. Questo vale solo per i tipi incorporati. Se si specifica un tipo esterno, l'utente sarà in grado di visualizzare i valori delle proprietà, ma non modificarlo.

 Tuttavia, è possibile specificare gli editor e i tipi seguenti:

1.  Un altro editor che viene usato con un tipo standard. Ad esempio, è possibile specificare un editor di percorso di file per una proprietà di stringa.

2.  Un tipo esterno per la proprietà di dominio e un editor.

3.  Un editor di .NET, ad esempio l'editor di percorso di file, oppure è possibile creare proprietà personalizzata dell'editor.

     La conversione tra un tipo esterno e un tipo come stringa, che dispone di un editor predefinito.

 In un linguaggio DSL, un *tipo esterno* è qualsiasi tipo che non è uno dei tipi semplici (ad esempio, valore booleano o Int32) o stringa.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Per definire una proprietà di dominio che dispone di un tipo esterno

1.  In **Esplora**, aggiungere un riferimento all'assembly (DLL) che contiene il tipo esterno, nel **Dsl** progetto.

     L'assembly può essere un assembly .NET o un assembly fornito dall'utente.

2.  Aggiungere il tipo per il **tipi di dominio** elenco, a meno che non è ancora stato fatto.

    1.  Aprire DslDefinition.dsl e in **Esplora DSL**pulsante destro del mouse il nodo radice e quindi fare clic su **Aggiungi nuovo tipo esterno**.

         Una nuova voce viene visualizzata sotto il **tipi di dominio** nodo.

        > [!WARNING]
        >  La voce di menu per il nodo radice DSL, non il **tipi di dominio** nodo.

    2.  Nella finestra Proprietà, impostare il nome e lo spazio dei nomi del nuovo tipo.

3.  Aggiungere una proprietà di dominio a una classe di dominio nel modo consueto.

     Nella finestra Proprietà, selezionare il tipo esterno dall'elenco a discesa nel **tipo** campo.

 In questa fase, gli utenti possono visualizzare i valori della proprietà, ma non possono modificarlo. I valori visualizzati vengono ottenuti le `ToString()` (funzione). È possibile scrivere codice programma che imposta il valore della proprietà, ad esempio in un comando o una regola.

### <a name="setting-a-property-editor"></a>L'impostazione di un Editor di proprietà
 Aggiungere un attributo CLR per la proprietà domain, nel formato seguente:

```
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 È possibile impostare l'attributo su una proprietà tramite il **attributo personalizzato** voce nella finestra Proprietà.

 Il tipo di `AnEditor` deve essere derivato dal tipo specificato nel secondo parametro. Il secondo parametro deve essere <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor>. Per altre informazioni, vedere <xref:System.ComponentModel.EditorAttribute>.

 È possibile specificare il proprio editor o un editor fornito nel [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ad esempio <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor>. Ad esempio, utilizzare la procedura seguente una proprietà in cui l'utente può immettere un nome di file.

##### <a name="to-define-a-file-name-domain-property"></a>Per definire una proprietà di dominio del nome file

1.  Aggiungere una proprietà di dominio a una classe di dominio nella propria definizione DSL.

2.  Selezionare la nuova proprietà. Nel **attributo personalizzato** campo nella finestra Proprietà, immettere il seguente attributo. Per immettere questo attributo, fare clic sui puntini di sospensione **[…]**  e quindi immettere il nome dell'attributo e i parametri separatamente:

    ```
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Lasciare l'impostazione predefinita di tipo della proprietà dominio **stringa**.

4.  Per testare l'editor, verificare che gli utenti possono aprire l'editor di nome file per modificare le proprietà del dominio.

    1.  Premere CTRL + F5 o F5. Nella soluzione di debug, aprire un file di test. Creare un elemento della classe di dominio e selezionarlo.

    2.  Nella finestra Proprietà selezionare la proprietà di dominio. Il campo del valore Mostra i puntini di sospensione **[…]** .

    3.  Fare clic sui puntini di sospensione. Verrà visualizzata una finestra di dialogo file. Selezionare un file e chiudere la finestra di dialogo. Il percorso del file è ora il valore della proprietà dominio.

### <a name="defining-your-own-property-editor"></a>Definizione di un editor di proprietà
 È possibile definire il proprio editor. È necessario farlo per consentire all'utente di modificare un tipo che è stato definito o per modificare un tipo di standard in modo speciale. Ad esempio, è possibile consentire all'utente di immettere una stringa che rappresenta una formula.

 Si definisce un editor scrivendo una classe derivata da <xref:System.Drawing.Design.UITypeEditor>. La classe deve eseguire l'override:

-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, per interagire con l'utente e aggiornare il valore della proprietà.

-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, per specificare se l'editor di aprire una finestra di dialogo o fornire un elenco a discesa.

 È anche possibile fornire una rappresentazione grafica del valore della proprietà che verrà visualizzato nella griglia delle proprietà. A tale scopo, eseguire l'override `GetPaintValueSupported`, e `PaintValue`.  Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Aggiungere il codice in un file di codice separato nella **Dsl** progetto.

 Ad esempio:

```
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}

```

 Per utilizzare questo editor, impostare il **attributo personalizzato** di una proprietà di dominio per:

```
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Fornisce un elenco di riepilogo a discesa di valori
 È possibile fornire un elenco di valori per un utente di scegliere.

> [!NOTE]
>  Questa tecnica fornisce un elenco di valori che possono cambiare in fase di esecuzione. Se si desidera fornire un elenco che non cambia, considerare invece l'utilizzo di un tipo enumerato come il tipo della proprietà di dominio.

 Per definire un elenco di valori standard, si aggiunge alla proprietà del dominio un attributo CLR che ha il formato seguente:

```
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]

```

 Definire una classe che deriva da <xref:System.ComponentModel.TypeConverter>. Aggiungere il codice in un file separato nella **Dsl** progetto. Ad esempio:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}

```

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)