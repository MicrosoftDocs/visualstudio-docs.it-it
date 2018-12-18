---
title: 'Procedura: aggiungere un comando al menu di scelta rapida'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2412e50279c646190d1112a42c00da06c75bf794
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Procedura: aggiungere un comando al menu di scelta rapida
È possibile aggiungere comandi di menu al linguaggio specifico di dominio (DSL) in modo che gli utenti possano effettuare attività specifiche per il DSL. I comandi sono visualizzati nel menu di scelta rapida quando gli utenti fanno clic con il pulsante destro del mouse sul diagramma. È possibile definire un comando in modo che venga visualizzato nel menu solo in situazioni specifiche, ad esempio solo quando l'utente fa clic su tipi specifici di elementi o su elementi con uno stato specifico.

 In sintesi, i passaggi vengono eseguiti nel progetto DslPackage come segue:

1.  [Dichiarare il comando in Commands.vsct](#VSCT)

2.  [Aggiornare il numero di versione del pacchetto nel Package.tt](#version). È necessario effettuare questa operazione ogni volta che si modifica Commands.vsct

3.  [Scrivere metodi nella classe CommandSet](#CommandSet) per rendere visibile il comando e per definire il comando desiderato.

 Per esempi, vedere il [sito Web di Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

> [!NOTE]
>  È inoltre possibile modificare il comportamento di alcuni comandi esistenti quali Taglia, Incolla, Seleziona tutto e Stampa eseguendo l'override dei metodi in CommandSet.cs. Per ulteriori informazioni, vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="defining-a-command-using-mef"></a>Definizione di un comando usando MEF
 Managed Extension Framework (MEF) fornisce un metodo alternativo per la definizione dei comandi di menu nel menu del diagramma. Il suo scopo principale è di consentire l'estensione di un DSL da parte dell'utente. Gli utenti possono scegliere di installare solo il DSL oppure sia il DSL sia le estensioni. Tuttavia, MEF riduce anche l'attività necessaria per definire i comandi del menu di scelta rapida, dopo l'attività iniziale di abilitazione di MEF sul DSL.

 Usare il metodo descritto in questo argomento se:

1.  Si vuole definire comandi di menu in menu diversi da quello di scelta rapida visualizzato facendo clic con il pulsante destro del mouse.

2.  Si vuole definire raggruppamenti specifici di comandi nel menu.

3.  Non si vuole consentire a terzi di estendere il DSL con comandi personalizzati.

4.  Si vuole definire un solo comando.

 In alternativa, valutare la possibilità di usare il metodo MEF per definire i comandi. Per ulteriori informazioni, vedere [estendere il modello DSL tramite MEF](../modeling/extend-your-dsl-by-using-mef.md).

##  <a name="VSCT"></a> Dichiarare il comando in Commands.Vsct
 I comandi di menu vengono dichiarati in DslPackage\Commands.vsct. Queste definizioni specificano le etichette delle voci di menu dove vengono visualizzate nei menu.

 Il file che si desidera modificare, Commands.vsct, Importa le definizioni da diversi file con estensione h, che si trovano nella directory *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Include inoltre GeneratedVsct.vsct, che viene generato dalla definizione DSL.

 Per ulteriori informazioni sui file con estensione vsct, vedere [Visual Studio Command Table (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>Per aggiungere il comando

1.  In **Esplora**, sotto il **DslPackage** del progetto, aprire Commands.vsct.

2.  Nell'elemento `Commands` definire uno o più pulsanti e un gruppo. Oggetto *pulsante* è un elemento del menu. Oggetto *gruppo* è disponibile una sezione del menu. Per definire queste voci, aggiungere gli elementi seguenti:

    ```
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    >  Ciascun pulsante o gruppo è identificato da un GUID e dall'ID di un numero intero. È possibile creare diversi gruppi e pulsanti con lo stesso GUID. Tuttavia, devono avere ID diversi. I nomi dei GUID e ID vengono convertiti in effettivo GUID e ID numerici nel `<Symbols>` nodo.

3.  Aggiungere un vincolo di visibilità per il comando in modo che venga caricato solo nel contesto del linguaggio specifico di dominio. Per ulteriori informazioni, vedere [VisibilityConstraints elemento](../extensibility/visibilityconstraints-element.md).

     Per eseguire questa operazione, aggiungere gli elementi seguenti all'elemento `CommandTable` dopo l'elemento `Commands`.

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4.  Definire i nomi da usare per i GUID e gli ID. Per eseguire questa operazione, aggiungere un elemento `Symbols` all'elemento `CommandTable` dopo l'elemento `Commands`.

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5.  Sostituire `{000...000}` con un GUID che identifica i gruppi e le voci di menu. Per ottenere un nuovo GUID, usare il **Crea GUID** strumento il **strumenti** menu.

    > [!NOTE]
    >  Se si aggiungono altri gruppi o altre voci di menu, è possibile usare lo stesso GUID. Tuttavia, è necessario usare nuovi valori per `IDSymbols`.

6.  Nel codice copiato da questa procedura, sostituire ogni occorrenza delle stringhe seguenti con le proprie stringhe:

    -   `grpidMyMenuGroup`

    -   `cmdidMyContextMenuCommand`

    -   `guidCustomMenuCmdSet`

    -   `My Context Menu Command`

##  <a name="version"></a> Aggiornare la versione del pacchetto in Package.tt
 Ogni volta che si aggiunge o si modifica un comando, aggiornare il parametro `version` della classe <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> applicata alla classe del pacchetto prima di rilasciare la nuova versione del linguaggio specifico di dominio.

 Poiché la classe del pacchetto è definita in un file generato, aggiornare l'attributo nel file del modello di testo che genera il file Package.cs.

#### <a name="to-update-the-packagett-file"></a>Per aggiornare il file Package.tt

1.  In **Esplora**nel **DslPackage** nel progetto il **GeneratedCode** cartella, aprire il file Package.tt.

2.  Trovare l'attributo `ProvideMenuResource`.

3.  Incrementare il parametro della `version` dell'attributo, che è il secondo parametro. Se si vuole, è possibile scrivere il nome del parametro in modo esplicito come promemoria del suo scopo. Ad esempio:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

##  <a name="CommandSet"></a> Definire il comportamento del comando
 Il DSL ha già alcuni comandi implementati in una classe parziale che è dichiarata in DslPackage\GeneratedCode\CommandSet.cs. Per aggiungere nuovi comandi è necessario estendere questa classe creando un nuovo file che contiene una dichiarazione parziale della stessa classe. Il nome della classe è in genere  *\<YourDslName >*`CommandSet`. È utile iniziare verificando il nome della classe ed esaminandone i contenuti.

 La classe del set di comandi è derivata da <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

#### <a name="to-extend-the-commandset-class"></a>Per estendere la classe del set di comandi

1.  In Esplora soluzioni, nel progetto DslPackage aprire la cartella GeneratedCode, cercare in CommandSet.tt e aprire il file CommandSet.cs generato. Prendere nota dello spazio dei nomi e del nome della prima classe definita qui. Può, ad esempio, essere visualizzato:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  In **DslPackage**, creare una cartella denominata **codice personalizzato**. In questa cartella, creare un nuovo file di classe denominato `CommandSet.cs`.

3.  Nel nuovo file scrivere una dichiarazione parziale con lo stesso spazio dei nomi e lo stesso nome della classe parziale generata. Ad esempio:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Nota** se si usa il modello di classe per creare il nuovo file, è necessario correggere lo spazio dei nomi sia il nome della classe.

### <a name="extend-the-command-set-class"></a>Estendere la classe di set di comandi
 Il codice del set di comandi deve in genere importare gli spazi dei nomi seguenti:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 Modificare lo spazio dei nomi e il nome della classe in modo che corrispondano a quelli del file CommandSet.cs generato:

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 È necessario definire due metodo, uno per stabilire quando sarà visibile il comando nel menu di scelta rapida e l'altro per eseguire il comando. Questi metodi non sono override, ma vengono registrati in un elenco di comandi.

### <a name="define-when-the-command-will-be-visible"></a>Definire quando sarà visibile il comando
 Per ogni comando, definire un metodo `OnStatus...` che stabilisce se il comando sarà visualizzato nel menu e se sarà abilitato o inattivo. Impostare le proprietà `Visible` e `Enabled` del `MenuCommand`, come mostrato nell'esempio seguente. Questo metodo è chiamato allo scopo di costruire il menu di scelta rapida ogni volta che l'utente fa clic con il pulsante destro del mouse sul diagramma, quindi deve funzionare rapidamente.

 In questo esempio il comando è visibile solo quando l'utente ha scelto un tipo specifico di forma ed è abilitato solo quando almeno uno degli elementi selezionati si trova in uno stato specifico. L'esempio è basato sul modello DSL del diagramma classi, e ClassShape e ModelClass sono tipi definiti nel DSL:

```
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 I frammenti seguenti sono spesso utili nei metodi OnStatus:

-   `this.CurrentSelection`. La forma su cui l'utente ha fatto clic con il pulsante destro del mouse è sempre inclusa in questo elenco. Se l'utente fa clic su una parte vuota del diagramma, il diagramma è l'unico membro dell'elenco.

-   `this.IsDiagramSelected()` - `true` Se l'utente fa clic su una parte vuota del diagramma.

-   `this.IsCurrentDiagramEmpty()`

-   `this.IsSingleSelection()` - l'utente non ha selezionato più forme.

-   `this.SingleSelection` - la forma o il diagramma su cui l'utente ha fatto clic con il pulsante destro del mouse.

-   `shape.ModelElement as MyLanguageElement` - l'elemento del modello rappresentato da una forma.

 Come linea guida generale, creare una dipendenza tra la proprietà `Visible` e il contenuto selezionato e creare una dipendenza tra la proprietà `Enabled` e lo stato degli elementi selezionati.

 Un metodo OnStatus non deve modificare lo stato dello store.

### <a name="define-what-the-command-does"></a>Definire l'azione del comando
 Per ogni comando, definire un metodo `OnMenu...` che esegua l'azione richiesta quando l'utente fa clic sul comando di menu.

 Se si apportano modifiche agli elementi del modello, è necessario effettuare questa operazione all'interno di una transazione. Per ulteriori informazioni, vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 In questo esempio, `ClassShape`, `ModelClass` e `Comment` sono tipi definiti nel DSL, che è derivato dal modello DSL del diagramma classi.

```
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Per ulteriori informazioni su come passare da un oggetto a un oggetto nel modello e su come creare gli oggetti e collegamenti, vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Registrare il comando
 Ripetere in C# le dichiarazioni dei valori GUID e id effettuate nella sezione Symbols di CommandSet.vsct:

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Utilizzare lo stesso valore GUID come è stato inserito **Commands.vsct**.

> [!NOTE]
>  Se si modifica la sezione Symbols del file VSCT, è necessario anche modificare queste dichiarazioni in modo corrispondente e incrementare il numero di versione in Package.tt.

 Registrare i comandi di menu come parte di questo set di comandi. `GetMenuCommands()` è chiamato una volta quando il diagramma viene inizializzato:

```
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Testare il comando
 Creare ed eseguire il DSL in un'istanza sperimentale di Visual Studio. Il comando viene visualizzato nel menu di scelta rapida nelle situazioni specificate.

#### <a name="to-exercise-the-command"></a>Per verificare il comando

1.  Nel **Esplora** sulla barra degli strumenti, fare clic su **Trasforma tutti i modelli**.

2.  Premere **F5** per ricompilare la soluzione e avviare il debug del linguaggio specifico di dominio nella compilazione sperimentale.

3.  Nella build sperimentale aprire un diagramma di esempio.

4.  Fare clic con il pulsante destro del mouse nel diagramma per verificare che il comando sia abilitato o disabilitato correttamente e visualizzato o nascosto in modo appropriato, a seconda dell'elemento selezionato.

## <a name="troubleshooting"></a>Risoluzione dei problemi
 **Comando non viene visualizzato nel menu di scelta:**

-   Il comando viene visualizzato solo nelle istanze di debug di Visual Studio, fino a quando si installa il pacchetto DSL. Per ulteriori informazioni, vedere [soluzioni per la distribuzione di un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).

-   Assicurarsi che il codice di esempio sperimentale presenti l'estensione del nome file corretto per il DSL. Per controllare l'estensione del nome file, aprire DslDefinition.dsl nell'istanza principale di Visual Studio. In Esplora DSL, fare clic con il pulsante destro del mouse sul nodo Editor, quindi fare clic su Proprietà. Nella finestra Proprietà esaminare la proprietà FileExtension.

-   È stata [incrementare il numero di versione del pacchetto](#version)?

-   Impostare un punto di interruzione all'inizio del metodo OnStatus. L'interruzione dovrebbe avvenire quando si fa clic con il pulsante destro del mouse su qualsiasi parte del diagramma.

     **Metodo OnStatus non viene chiamato**:

    -   Assicurarsi che i GUID e gli ID del codice CommandSet corrispondano a quelli della sezione Symbols di Commands.vsct.

    -   In Commands.vsct verificare che il GUID e l'ID di ogni nodo padre identifichino il gruppo padre corretto.

    -   In un prompt dei comandi di Visual Studio digitare devenv /rootsuffix exp /setup, quindi riavviare l'istanza di debug di Visual Studio.

-   Eseguire il metodo OnStatus per verificare che command.Visible e command.Enabled siano impostati su true.

 **Viene visualizzato il testo del menu errato o comando viene visualizzata nella posizione sbagliata**:

-   Assicurarsi che la combinazione di GUID e ID sia univoca per questo comando.

-   Assicurarsi di aver disinstallato versioni precedenti del pacchetto.

## <a name="see-also"></a>Vedere anche

- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md)
- [Codice di esempio: diagrammi circuito](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]