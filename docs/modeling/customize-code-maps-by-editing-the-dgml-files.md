---
title: Personalizzare le mappe codice modificando i file DGML
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7ee92121e57b7c3f6391d290ff0c5fde0d689e3c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Personalizzare le mappe del codice modificando i file DGML
Per personalizzare una mappa di codice, è possibile modificare il file Directed Graph Markup Language (con estensione dgml) di una mappa. È ad esempio possibile modificare elementi per specificare stili personalizzati, assegnare proprietà e categorie a collegamenti e elementi di codice o collegare documenti o URL a elementi di codice o a collegamenti.  Per ulteriori informazioni sugli elementi DGML, vedere [riferimento diretto Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md).

 Modificare il file con estensione dgml della mappa di codice in un editor di testo o XML. Se la mappa fa parte della soluzione di Visual Studio, selezionarlo in **Esplora**, aprire il menu di scelta rapida e scegliere **Apri con**, **Editor XML (testo)**.

> [!NOTE]
>  Per creare mappe codice, è necessario usare Visual Studio Enterprise. Quando si modifica una mappa di codice in Visual Studio, viene eseguita la rimozione di tutti gli attributi e gli elementi DGML inutilizzati che vengono eliminati quando si salva il file con estensione dgml. Vengono anche creati automaticamente elementi di codice quando si aggiungono manualmente nuovi collegamenti. Quando si salva il file con estensione dgml, tutti gli attributi aggiunti a un elemento si ridispongono in ordine alfabetico.

##  <a name="OrganizeNodes"></a> Raggruppare gli elementi di codice
 È possibile aggiungere nuovi gruppi o convertire i nodi esistenti in un gruppo.

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Per convertire un elemento di codice in un gruppo, trovare l'elemento `<Node/>` per tale elemento di codice.

     \- oppure -

     Per aggiungere un nuovo gruppo, individuare la sezione `<Nodes>`. Aggiungere un nuovo elemento `<Node/>`.

3.  Nell'elemento `<Node/>` aggiungere un attributo `Group` per specificare se il gruppo viene visualizzato espanso o compresso. Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyFirstGroup" Group="Expanded" />
       <Node Id="MySecondGroup" Group="Collapsed" />
    </Nodes>
    ```

4.  Nella sezione `<Links>` verificare che sia presente un elemento `<Link/>` con gli attributi seguenti per ogni relazione tra un elemento di codice di gruppo e i relativi elementi figlio:

    -   Un attributo `Source` che specifica l'elemento di codice di gruppo

    -   Un attributo `Target` che specifica l'elemento di codice figlio

    -   Un attributo `Category` che specifica una relazione `Contains` tra l'elemento di codice di gruppo e il relativo elemento figlio

     Ad esempio:

    ```xml
    <Links>
       <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
       <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
       <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
       <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
    </Links>
    ```

     Per ulteriori informazioni sul `Category` attributo, vedere [assegnare le categorie per gli elementi di codice e collegamenti](#AssignCategories).

##  <a name="ChangeGraphStyle"></a> Modificare lo stile della mappa
 È possibile modificare il colore di sfondo e del bordo della mappa modificando il file con estensione dgml della mappa. Per modificare lo stile di elementi di codice e collegamenti, vedere [modificare lo stile di elementi di codice e collegamenti](#Highlight).

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Nell'elemento `<DirectedGraph>` aggiungere uno qualsiasi dei seguenti attributi per modificarne lo stile:

     Colore di sfondo

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Colore bordo

    ```xml
    Stroke="StrokeValue"
    ```

     Ad esempio:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

##  <a name="Highlight"></a> Modificare lo stile di elementi di codice e collegamenti

###  <a name="CreateCustomStyles"></a>
 È possibile applicare stili personalizzati agli elementi di codice seguenti:

-   Singoli elementi di codice e collegamenti

-   Gruppi di elementi di codice e collegamenti

-   Gruppi di elementi di codice e collegamenti in base a determinate condizioni

> [!TIP]
>  Se sono presenti stili ripetuti in molti elementi di codice o collegamenti, è possibile applicare una categoria quegli elementi di codice oppure ai collegamenti e quindi applicare uno stile a quella categoria. Per ulteriori informazioni, vedere [assegnare categorie per gli elementi di codice e collegamenti](#AssignCategories) e [assegnare proprietà per gli elementi di codice e collegamenti](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Per applicare uno stile personalizzato a un singolo elemento di codice

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Node/>` dell'elemento di codice. Aggiungere uno qualsiasi di questi attributi per personalizzarne lo stile:

     Colore di sfondo

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Struttura

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Spessore del contorno

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Colore del testo

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Icona

    ```xml
    Icon="IconFilePathLocation"
    ```

     Dimensione del testo

    ```xml
    FontSize="FontSizeValue"
    ```

     Tipo di testo

    ```xml
    FontFamily="FontFamilyName"
    ```

     Spessore del testo

    ```xml
    FontWeight="FontWeightValue"
    ```

     Stile del testo

    ```xml
    FontStyle="FontStyleName"
    ```

     È possibile, ad esempio, specificare `Italic` come stile del testo.

     Trama

    ```xml
    Style="Glass"
    ```

     - oppure -

    ```xml
    Style="Plain"
    ```

     Forma

     Per sostituire una forma con un'icona, impostare la proprietà `Shape` su `None` e la proprietà `Icon` sul percorso con il file dell'icona.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Per applicare uno stile personalizzato a un singolo collegamento

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Link/>` che contiene i nomi dell'elemento di codice sorgente e di quello di destinazione.

3.  Nell'elemento `<Link/>` aggiungere uno qualsiasi dei seguenti attributi per personalizzarne lo stile:

     Colore di contorno e punta della freccia

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Spessore del contorno

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Stile del contorno

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Ad esempio:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Per applicare stili personalizzati a un gruppo di elementi di codice o collegamenti

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Se non è presente un elemento `<Styles></Styles>`, aggiungerne uno sotto l'elemento `<DirectedGraph></DirectedGraph>` dopo l'elemento `<Links></Links>`.

3.  Nell'elemento `<Styles></Styles>`, sotto l'elemento `<Style/>`, specificare gli attributi seguenti:

    -   `TargetType="Node` &#124; `Link | Graph"`

    -   `GroupLabel="` *NameInLegendBox* `"`

    -   `ValueLabel="` *NameInStylePickerBox* `"`

     Per applicare un stile personalizzato a tutti i tipi di destinazione, non usare una condizione.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Per applicare stili condizionali a un gruppo di elementi di codice o collegamenti

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Nell'elemento `<Style/>` aggiungere un elemento `<Condition/>` contenente un attributo `Expression` per specificare un'espressione che restituisca un valore booleano.

     Ad esempio:

    ```xml
    <Condition Expression="MyCategory"/>
    ```

     - oppure -

    ```xml
    <Condition Expression="MyCategory > 100"/>
    ```

     - oppure -

    ```xml
    <Condition Expression="HasCategory('MyCategory')"/>
    ```

     Questa espressione utilizza la notazione BNF (Backus-Naur Form) seguente:

     <Expression> ::= <BinaryExpression> &#124; <UnaryExpression> &#124; "("<Expression>")" &#124; <MemberBindings> &#124; <Literal> &#124; <Number>

     <BinaryExpression> ::= <Expression> <Operator> <Expression>

     <UnaryExpression> ::= "!" <Expression> &#124; "+" <Expression> &#124; "-" <Expression>

     <Operator> ::= "<" &#124; "\<=" &#124; "=" &#124; ">=" &#124; ">" &#124; "!=" &#124; "or" &#124; "and" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

     <MemberBindings> ::= <MemberBindings> &#124; <MemberBinding> "." <MemberBinding>

     <MemberBinding> ::= <MethodCall> &#124; <PropertyGet>

     <MethodCall> ::= <Identifier> "(" <MethodArgs> ")"

     <PropertyGet> :: = Identificatore

     <MethodArgs> ::= <Expression> &#124; <Expression> "," <MethodArgs> &#124; <empty>

     <Identifier> ::= [^. ]*

     <Literal> :: = valore letterale stringa singola o tra virgolette doppie

     <Number> :: = stringa di cifre con virgola decimale facoltativa

     È possibile specificare più `<Condition/>` elementi che devono essere tutti true per applicare lo stile.

3.  Sulla riga successiva dopo l'elemento `<Condition/>`, aggiungere uno o più elementi `<Setter/>` per specificare un attributo `Property` e un attributo fisso `Value` o un attributo `Expression` calcolato da applicare alla mappa, agli elementi di codice o ai collegamenti che soddisfano la condizione.

     Ad esempio:

    ```xml
    <Setter Property="BackGround" Value="Green"/>
    ```

 Per fare un semplice esempio completo, la condizione seguente specifica che un elemento di codice viene visualizzato in verde o in rosso a seconda che la categoria `Passed` sia impostata su `True` o su `False`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Nella tabella seguente sono incluse alcune condizioni di esempio che è possibile usare:

 Impostare la dimensione del carattere come una funzione del numero di righe di codice che modifica anche la dimensione dell'elemento di codice. In questo esempio viene usata una sola espressione condizionale per impostare più proprietà, `FontSize` e `FontFamily`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Impostare il colore di sfondo di un elemento di codice in base alla proprietà `Coverage`. Gli stili vengono valutati nell'ordine in cui appaiono, in modo analogo alle istruzioni `if-else`.

 In questo esempio:

1.  Se `Coverage` è > 80, impostare la proprietà `Background` su verde.

2.  Se invece `Coverage` è > 50, impostare la proprietà `Background` su una sfumatura di arancione in base al valore della proprietà `Coverage`.

3.  Diversamente impostare la proprietà `Background` su una sfumatura di rosso in base al valore della proprietà `Coverage`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Impostare la proprietà `Shape` su `None`, in modo che l'icona sostituisca la forma. Usare la proprietà `Icon` per specificare la posizione dell'icona.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

##  <a name="AssignProperties"></a> Assegnare le proprietà per i collegamenti e gli elementi di codice
 È possibile organizzare elementi di codice e collegamenti mediante l'assegnazione di proprietà. Ad esempio, è possibile selezionare elementi di codice con proprietà specifiche in modo che sia possibile raggrupparli, modificarne lo stile o nasconderli.

#### <a name="to-assign-a-property-to-a-code-element"></a>Per assegnare una proprietà a un elemento di codice

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Node/>` per tale elemento di codice. Specificare il nome della proprietà e il relativo valore. Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3.  Aggiungere un elemento `<Property/>` alla sezione `<Properties>` per specificare attributi quali il nome visibile e il tipo di dati:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Per assegnare una proprietà a un collegamento

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Link/>` che contiene i nomi dell'elemento di codice sorgente e di quello di destinazione.

3.  Nell'elemento `<Node/>` specificare il nome della proprietà e il relativo valore. Ad esempio:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4.  Aggiungere un elemento `<Property/>` alla sezione `<Properties>` per specificare attributi quali il nome visibile e il tipo di dati:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

##  <a name="AssignCategories"></a> Assegnare le categorie per i collegamenti e gli elementi di codice
 Nelle sezioni seguenti viene illustrato come è possibile organizzare elementi di codice mediante l'assegnazione di categorie e come è possibile creare categorie gerarchiche che consentono di organizzare elementi di codice e aggiungere attributi alle categorie figlio tramite l'ereditarietà.

#### <a name="to-assign-a-category-to-a-code-element"></a>Per assegnare una categoria a un elemento di codice

-   Aprire il file con estensione dgml in un editor di testo o XML.

-   Individuare l'elemento `<Node/>` per l'elemento di codice desiderato.

-   Nell'elemento `<Node/>` aggiungere un attributo `Category` per specificare il nome della categoria. Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Aggiungere un elemento `<Category/>` alla sezione `<Categories>` in modo che sia possibile usare l'attributo `Label` per specificare il testo visualizzato per tale categoria:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Per assegnare una categoria a un collegamento

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Link/>` che contiene i nomi dell'elemento di codice sorgente e di quello di destinazione.

3.  Nell'elemento `<Link/>` aggiungere un attributo `Category` per specificare il nome della categoria. Ad esempio:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4.  Aggiungere un elemento `<Category/>` alla sezione `<Categories>` in modo che sia possibile usare l'attributo `Label` per specificare il testo visualizzato per tale categoria:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Per creare categorie gerarchiche

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Aggiungere un elemento `<Category/>` per la categoria padre, quindi aggiungere l'attributo `BasedOn` all'elemento `<Category/>` della categoria figlio.

     Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     In questo esempio lo sfondo di `MyFirstNode` è verde perché il relativo attributo `Category` eredita l'attributo `Background` di `MyParentCategory`.

##  <a name="AddReferences"></a> Documenti di collegamento o URL a elementi di codice e collegamenti
 È possibile collegare documenti o URL a un elemento di codice oppure a collegamenti modificando il file con estensione dgml della mappa e aggiungendo un attributo `Reference` all'elemento `<Node/>` per un elemento di codice oppure all'elemento `<Link/>` per un collegamento. È quindi possibile aprire e visualizzare il contenuto dall'elemento di codice o dal collegamento. L'attributo `Reference` specifica il percorso di tale contenuto. Il percorso può essere assoluto oppure relativo alla posizione del file con estensione dgml.

> [!CAUTION]
>  Se si usano percorsi relativi e se il file con estensione dgml viene spostato in un percorso diverso, i percorsi non saranno più risolvibili. Quando si tenta di aprire e visualizzare il contenuto collegato, si verificherà un errore che informa che il contenuto non può essere visualizzato.

 Ad esempio, è possibile collegare i seguenti elementi di codice:

-   Per descrivere le modifiche apportate a una classe, è possibile collegare l'URL di un elemento di codice di lavoro, un documento o un altro file con estensione dgml all'elemento di codice relativo a una classe.

-   È possibile collegare un diagramma di dipendenza a un elemento di codice di gruppo che rappresenta un livello nell'architettura logica del software.

-   Per visualizzare altre informazioni su un componente che espone un'interfaccia, è possibile collegare un diagramma dei componenti all'elemento di codice relativo a tale interfaccia.

-   Collegare un elemento di codice a un elemento di lavoro di Team Foundation Server o i bug o altre informazioni correlate all'elemento di codice.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Per collegare un documento o un URL a un elemento di codice

1.  Aprire il file con estensione dgml in un editor di testo o XML.

2.  Individuare l'elemento `<Node/>` per l'elemento di codice desiderato.

3.  Eseguire una delle attività elencate nella tabella seguente:

     Un elemento di codice singolo

    -   Nell'elemento `<Node/>` o `<Link/>` aggiungere un attributo `Reference` per specificare la posizione dell'elemento di codice.

        > [!NOTE]
        >  È possibile specificare un solo attributo `Reference` per elemento.

     Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyNode" Reference="MyDocument.txt" />
    </Nodes>
    <Properties>
       <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
    </Properties>
    ```

     Più elementi di codice

    1.  Nell'elemento `<Node/>` o `<Link/>` aggiungere un nuovo attributo per specificare la posizione di ogni riferimento.

    2.  Nella sezione `<Properties>`:

        1.  Aggiungere un elemento `<Property/>` per ogni nuovo tipo di riferimento.

        2.  Impostare l'attributo `Id` sul nome dell'attributo del nuovo riferimento.

        3.  Aggiungere il `IsReference` attributo e impostarlo su `True` per visualizzare il riferimento dell'elemento di codice **Vai a riferimento** menu di scelta rapida.

        4.  Utilizzare il `Label` attributo per specificare il testo visualizzato per l'elemento di codice **Vai a riferimento** menu di scelta rapida.

     Ad esempio:

    ```xml
    <Nodes>
       <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
    </Nodes>
    <Properties>
       <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
       <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
    </Properties>
    ```

     Sulla mappa il nome dell'elemento di codice viene visualizzato sottolineato. Quando si apre il menu di scelta rapida per l'elemento di codice o il collegamento, verrà visualizzato un **Vai a riferimento** menu di scelta rapida che contiene gli elementi del codice collegate da scegliere.

4.  Usare l'attributo `ReferenceTemplate` per specificare una stringa comune, ad esempio un URL, usata da più riferimenti anziché ripetere tale stringa nel riferimento.

     L'attributo `ReferenceTemplate` specifica un segnaposto per il valore del riferimento. Nell'esempio seguente il segnaposto `{0}` nell'attributo `ReferenceTemplate` verrà sostituito dai valori degli attributi `MyFirstReference` e `MySecondReference` nell'elemento `<Node/>` per produrre un percorso completo:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
       <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
    </Nodes>
    <Properties>
       <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
       <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
    </Properties>
    ```

5.  Per visualizzare l'elemento o gli elementi di codice cui si fa riferimento, aprire il menu di scelta rapida per l'elemento di codice o il collegamento. Scegliere **Vai a riferimento** e quindi l'elemento di codice.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
- [Riferimento di Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
