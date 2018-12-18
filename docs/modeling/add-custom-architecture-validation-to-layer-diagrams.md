---
title: Aggiunta di convalida dell'architettura personalizzati a diagrammi di dipendenza
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3fbc4762e1bf5f08b81b884d2a8acea2f16283ed
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Aggiunta di convalida dell'architettura personalizzati a diagrammi di dipendenza
In Visual Studio, gli utenti possono convalidare il codice sorgente in un progetto rispetto a un modello di livello in modo da poter verificare che il codice sorgente sia conforme alla dipendenze in un diagramma di dipendenze. Benché sia disponibile un algoritmo di convalida standard, è possibile definire estensioni di convalida personalizzate.

 Quando l'utente seleziona il **Convalida architettura** comando in un diagramma di dipendenza, viene richiamato il metodo di convalida standard, seguito dalle eventuali estensioni di convalida che sono stati installati.

> [!NOTE]
>  In un diagramma di dipendenze, lo scopo principale di convalida consiste nel confrontare il diagramma con il codice programma in altre parti della soluzione.

 È possibile creare un pacchetto dell'estensione di convalida dei livelli in un progetto VSIX (Visual Studio Integration Extension), che è possibile distribuire ad altri utenti di Visual Studio. È possibile inserire solo il validator in un progetto VSIX oppure combinarlo con altre estensioni nello stesso progetto VSIX. È consigliabile scrivere il codice del validator in un progetto di Visual Studio a se stante anziché nello stesso progetto di altre estensioni.

> [!WARNING]
>  Dopo aver creato un progetto di convalida, copiare il [codice di esempio](#example) disponibile alla fine di questo argomento e quindi modificarlo in base alle esigenze.

## <a name="requirements"></a>Requisiti
 Vedere [Requisiti](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definizione di un validator dei livelli in un nuovo progetto VSIX
 Il modo più rapido per creare un validator è usare il modello di progetto. In questo modo il codice e il manifesto VSIX vengono inseriti nello stesso progetto.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Per definire un'estensione tramite un modello di progetto

1.  Creare un progetto in una nuova soluzione usando il comando **Nuovo progetto** del menu **File** .

2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Estensione di convalida progettazione livelli**in **Progetti di modellazione**.

     Il modello crea un progetto che contiene un piccolo esempio.

    > [!WARNING]
    >  Al modello makethe funzionamento:
    >
    >  -   Modificare le chiamate a `LogValidationError` in modo da rimuovere gli argomenti facoltativi `errorSourceNodes` e `errorTargetNodes`.
    > -   Se si utilizzano le proprietà personalizzate, applicare l'aggiornamento indicato in [aggiungere proprietà personalizzate ai diagrammi dipendenza](../modeling/add-custom-properties-to-layer-diagrams.md).

3.  Modificare il codice per definire la convalida. Per altre informazioni, vedere [Programmazione della convalida](#programming).

4.  Per testare l'estensione, vedere [Debug della convalida dei livelli](#debugging).

    > [!NOTE]
    >  Il metodo verrà chiamato solo in casi specifici e i punti di interruzione non funzioneranno automaticamente. Per altre informazioni, vedere [Debug della convalida dei livelli](#debugging).

5.  Per installare l'estensione nell'istanza principale di Visual Studio o in un altro computer, trovare il **VSIX** file **bin\\\***. Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallare l'estensione, usare l'opzione **Estensioni e aggiornamenti** del menu **Strumenti** .

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Aggiunta di validator dei livelli a un progetto VSIX separato
 Se si vuole creare un progetto VSIX contenente validator dei livelli, comandi e altre estensioni, è consigliabile creare un unico progetto per definire l'estensione VSIX e progetti separati per i gestori.

#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Per aggiungere la convalida dei livelli a un progetto VSIX separato

1.  Creare un progetto di libreria di classi in una soluzione di Visual Studio nuova o esistente. Nella finestra di dialogo **Nuovo progetto** fare clic su **Visual C#** e quindi su **Libreria di classi**. Questo progetto conterrà la classe di convalida dei livelli.

2.  Identificare o creare un progetto VSIX nella soluzione. Un progetto VSIX contiene un file denominato **source.extension.vsixmanifest**. Se è necessario aggiungere un progetto VSIX, eseguire le operazioni seguenti:

    1.  Nella finestra di dialogo **Nuovo progetto** scegliere **Visual C#**, **Extensibility**e **Progetto VSIX**.

    2.  In **Esplora soluzioni**scegliere **Imposta come progetto di avvio**dal menu di scelta rapida del progetto VSIX.

3.  In **source.extension.vsixmanifest**aggiungere il progetto di convalida dei livelli come componente MEF in **Asset**.

    1.  Scegliere **Nuovo**.

    2.  Nella finestra di dialogo **Aggiungi nuovo asset** impostare:

         **Tipo** = **Microsoft.VisualStudio.MefComponent**

         **Origine** = **Progetto nella soluzione corrente**

         **Progetto** = *Progetto di convalida*

4.  È anche necessario aggiungere il progetto come convalida dei livelli:

    1.  Scegliere **Nuovo**.

    2.  Nella finestra di dialogo **Aggiungi nuovo asset** impostare:

         **Tipo** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Questa opzione non è inclusa nell'elenco a discesa. È necessario immetterla usando la tastiera.

         **Origine** = **Progetto nella soluzione corrente**

         **Progetto** = *Progetto di convalida*

5.  Tornare al progetto di convalida dei livelli e aggiungere i riferimenti al progetto seguenti:

    |**Riferimento**|**Operazioni consentite**|
    |-------------------|------------------------------------|
    |Microsoft.VisualStudio.GraphModel.dll|Leggere il grafico dell'architettura|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Leggere il code DOM associato ai livelli|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Leggere il modello di livello|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Leggere e aggiornare forme e diagrammi|
    |System.ComponentModel.Composition|Definire il componente di convalida mediante Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[versione]|Definire le estensioni di modellazione|

6.  Copiare il codice di esempio disponibile alla fine di questo argomento nel file di classe nel progetto della libreria del validator in modo che contenga il codice per la convalida. Per altre informazioni, vedere [Programmazione della convalida](#programming).

7.  Per testare l'estensione, vedere [Debug della convalida dei livelli](#debugging).

    > [!NOTE]
    >  Il metodo verrà chiamato solo in casi specifici e i punti di interruzione non funzioneranno automaticamente. Per altre informazioni, vedere [Debug della convalida dei livelli](#debugging).

8.  Per installare l'estensione VSIX nell'istanza principale di Visual Studio o in un altro computer, trovare il **VSIX** file nel **bin** directory del progetto VSIX. Copiare il file nel computer in cui si vuole installare il progetto VSIX. Fare doppio clic sul file VSIX in Esplora risorse

     Per disinstallare l'estensione, usare l'opzione **Estensioni e aggiornamenti** del menu **Strumenti** .

##  <a name="programming"></a> Programmazione della convalida
 Per definire un'estensione di convalida dei livelli, è necessario definire una classe con le caratteristiche seguenti:

-   Il formato complessivo della dichiarazione è il seguente:

    ```

    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
    using Microsoft.VisualStudio.GraphModel;
    ...
     [Export(typeof(IValidateArchitectureExtension))]
      public partial class Validator1Extension :
                      IValidateArchitectureExtension
      {
        public void ValidateArchitecture(Graph graph)
        {
           GraphSchema schema = graph.DocumentSchema;
          ...
      } }
    ```

-   Quando si individua un errore, è possibile segnalarlo usando `LogValidationError()`.

    > [!WARNING]
    >  Non usare i parametri facoltativi di `LogValidationError`.

 Quando l'utente richiama il comando di menu **Convalida architettura** , il sistema di runtime dei livelli analizza i livelli e i rispettivi elementi per generare un grafico. Il grafico è costituito da quattro parti:

-   I modelli di livello della soluzione Visual Studio che sono rappresentati come nodi e collegamenti nel grafico.

-   Il codice, gli elementi di progetto e altri elementi definiti nella soluzione e rappresentati come nodi, insieme ai collegamenti che rappresentano le dipendenze individuate dal processo di analisi.

-   I collegamenti dai nodi di livello ai nodi elemento del codice.

-   I nodi che rappresentano gli errori individuati dal validator.

 Una volta creato il grafico, viene chiamato il metodo di convalida standard. Al termine, tutti i metodi di convalida delle eventuali estensioni installate vengono chiamati in base a un ordine non specificato. Il grafico viene passato a ogni metodo `ValidateArchitecture` , che può analizzarlo e segnalare gli eventuali errori trovati.

> [!NOTE]
>  Questo non è lo stesso processo di convalida che può essere usato in linguaggi specifici del dominio.

 I metodi di convalida non devono modificare il modello di livello o il codice convalidato.

 Il modello di grafico è definito in <xref:Microsoft.VisualStudio.GraphModel>. Le classi principali sono <xref:Microsoft.VisualStudio.GraphModel.GraphNode> e <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

 Ogni nodo e ogni collegamento hanno una o più categorie che specificano il tipo di elemento o la relazione che rappresenta. I nodi di un grafico tipico hanno le categorie seguenti:

-   Dsl.LayerModel

-   Dsl.Layer

-   Dsl.Reference

-   CodeSchema_Type

-   CodeSchema_Namespace

-   CodeSchema_Type

-   CodeSchema_Method

-   CodeSchema_Field

-   CodeSchema_Property

 I collegamenti dai livelli agli elementi nel codice sono associati alla categoria "Rappresenta".

##  <a name="debugging"></a> Debug della convalida
 Per eseguire il debug dell'estensione di convalida dei livelli, premere CTRL+F5. Viene aperta un'istanza sperimentale di Visual Studio. In questa istanza aprire o creare un modello di livello. Questo modello deve essere associato al codice e deve avere almeno una dipendenza.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Eseguire il test con una soluzione che contiene dipendenze
 La convalida non viene eseguita se non sono presenti le caratteristiche seguenti:

-   È presente almeno un collegamento di dipendenza nel diagramma di dipendenza.

-   Alcuni livelli nel modello sono associati a elementi del codice.

 La prima volta che si avvia un'istanza sperimentale di Visual Studio per testare l'estensione di convalida, aprire o creare una soluzione che abbia queste caratteristiche.

### <a name="run-clean-solution-before-validate-architecture"></a>Eseguire Pulisci soluzione prima di Convalida architettura
 Ogni volta che si aggiorna il codice di convalida, usare il comando **Pulisci soluzione** del menu **Compila** nella soluzione sperimentale prima di testare il comando Convalida. Questa operazione è necessaria perché i risultati della convalida vengono memorizzati nella cache. Se il diagramma di dipendenze di test o il relativo codice di avere non aggiornato, i metodi di convalida non essere eseguiti.

### <a name="launch-the-debugger-explicitly"></a>Avviare il debugger in modo esplicito
 La convalida viene eseguita in un processo separato. Di conseguenza, i punti di interruzione nel metodo di convalida non verranno attivati. È necessario connettere il debugger al processo in modo esplicito all'avvio della convalida.

 Per connettere il debugger al processo di convalida, inserire una chiamata a `System.Diagnostics.Debugger.Launch()` all'avvio del metodo di convalida. Quando viene visualizzata la finestra di dialogo Debug, selezionare l'istanza principale di Visual Studio.

 In alternativa, è possibile inserire una chiamata a `System.Windows.Forms.MessageBox.Show()`. Quando viene visualizzata la finestra di messaggio, passare all'istanza principale di Visual Studio e scegliere il **Debug** dal menu **Connetti a processo**. Selezionare il processo denominato **Graphcmd.exe**.

 Avviare sempre l'istanza sperimentale premendo CTRL+F5 (**Avvia senza eseguire debug**).

### <a name="deploying-a-validation-extension"></a>Distribuzione di un'estensione di convalida
 Per installare l'estensione di convalida in un computer in cui è installata una versione appropriata di Visual Studio, aprire il file VSIX nel computer di destinazione. Per eseguire l'installazione in un computer in cui è installato [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] , è necessario estrarre manualmente il contenuto VSIX in una cartella Extensions. Per ulteriori informazioni, vedere [distribuire un'estensione del modello di livello](../modeling/deploy-a-layer-model-extension.md).

##  <a name="example"></a> Example code

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
