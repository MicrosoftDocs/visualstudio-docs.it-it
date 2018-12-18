---
title: 'Procedura dettagliata: Generazione di codice tramite modelli di testo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 46cbf0c6a28b10434ed364dffd77c4c01620d6ea
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Procedura dettagliata: generazione di codice tramite modelli di testo
La generazione del codice consente di creare codice di programma fortemente tipizzato e al tempo stesso facilmente modificato quando viene modificato il modello di origine. Ciò si differenzia dalla tecnica alternativa di scrivere un programma completamente generico che accetta un file di configurazione, che è più flessibile, ma genera codice più difficile da leggere e modificare e caratterizzato da prestazioni inferiori. Questa procedura dettagliata illustra tale vantaggio.  
  
## <a name="typed-code-for-reading-xml"></a>Codice tipizzato per leggere l'XML  
 Lo spazio dei nomi System. XML fornisce strumenti completi per il caricamento di un documento XML e quindi la sua libera navigazione in memoria. Sfortunatamente tutti i nodi hanno lo stesso tipo, XmlNode. È pertanto molto facile commettere errori di programmazione, ad esempio aspettarsi il tipo sbagliato di nodo figlio o gli attributi errati.  
  
 In questo progetto di esempio un modello legge un file XML di esempio e genera classi che corrispondono a ogni tipo di nodo. Nel codice scritto a mano è possibile usare queste classi per passare al file XML. È anche possibile eseguire l'applicazione su qualsiasi altro file che usa gli stessi tipi di nodo. Lo scopo del file XML di esempio è fornire esempi di tutti i tipi di nodo con cui l'applicazione dovrà avere a che fare.  
  
> [!NOTE]
>  L'applicazione [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), inclusa in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], può generare classi fortemente tipizzate da file XML. Il modello illustrato qui viene fornito come esempio.  
  
 Ecco il file di esempio:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<catalog>  
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">  
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>  
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>  
  </artist>  
  <artist id ="Euan%20Garden" name="Euan Garden">  
    <song id ="GardenScottishCountry">Scottish Country Garden</song>  
  </artist>  
</catalog>  
```  
  
 Nel progetto costruito da questa procedura dettagliata è possibile scrivere codice simile al seguente e IntelliSense suggerisce i nomi di attributo e figlio corretti durante la digitazione:  
  
```  
Catalog catalog = new Catalog(xmlDocument);  
foreach (Artist artist in catalog.Artist)  
{  
  Console.WriteLine(artist.name);  
  foreach (Song song in artist.Song)  
  {  
    Console.WriteLine("   " + song.Text);  
  }  
}  
```  
  
 Ciò si differenzia dal codice non tipizzato che è possibile scrivere senza il modello:  
  
```  
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");  
foreach (XmlNode artist in catalog.SelectNodes("artist"))  
{  
    Console.WriteLine(artist.Attributes["name"].Value);  
    foreach (XmlNode song in artist.SelectNodes("song"))  
    {  
         Console.WriteLine("   " + song.InnerText);  
     }  
}  
```  
  
 Nella versione fortemente tipizzata una modifica allo schema XML comporterà modifiche alle classi. Il compilatore evidenzierà le parti del codice dell'applicazione che devono essere modificate. Tale supporto non è disponibile nella versione non tipizzata che usa il codice XML generico.  
  
 In questo progetto viene usato un singolo file di modello per generare le classi che rendono possibile la versione tipizzata.  
  
## <a name="setting-up-the-project"></a>Configurazione del progetto  
  
### <a name="create-or-open-a-c-project"></a>Creare o aprire un progetto C#  
 È possibile applicare questa tecnica a qualsiasi progetto di codice. Questa procedura dettagliata usa un progetto C# e ai fini di test si userà un'applicazione console.  
  
##### <a name="to-create-the-project"></a>Per creare il progetto  
  
1.  Nel menu **File** fare clic su **Nuovo** e poi su **Progetto**.  
  
2.  Fare clic sul nodo **Visual C#** e poi, nel riquadro **Modelli** , su **Applicazione console**.  
  
### <a name="add-a-prototype-xml-file-to-the-project"></a>Aggiungere un file XML prototipo al progetto  
 Lo scopo di questo file è fornire esempi dei tipi di nodo XML che l'applicazione dovrà poter leggere. Potrebbe trattarsi di un file che sarà usato per il test dell'applicazione. Il modello genererà una classe C# per ogni tipo di nodo in questo file.  
  
 Il file deve far parte del progetto in modo che il modello possa leggerlo, ma non sarà integrato nell'applicazione compilata.  
  
##### <a name="to-add-an-xml-file"></a>Per aggiungere un file XML  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, fare clic su **Aggiungi** e quindi su **Nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **File XML** dal riquadro **Modelli** .  
  
3.  Aggiungere il contenuto di esempio al file.  
  
4.  Per questa procedura dettagliata assegnare al file il nome `exampleXml.xml`. Impostare il contenuto del file in modo che sia l'XML mostrato nella sezione precedente.  
  
 .  
  
### <a name="add-a-test-code-file"></a>Aggiungere un file di codice di test  
 Aggiungere al progetto un file C# e scrivere in esso un esempio del codice che si vuole poter scrivere. Ad esempio:  
  
```  
using System;  
namespace MyProject  
{  
  class CodeGeneratorTest  
  {  
    public void TestMethod()  
    {  
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");  
      foreach (Artist artist in catalog.Artist)  
      {  
        Console.WriteLine(artist.name);  
        foreach (Song song in artist.Song)  
        {  
          Console.WriteLine("   " + song.Text);  
} } } } }  
```  
  
 In questa fase la compilazione del codice non riuscirà. Scrivendo il modello, saranno generate classi che consentiranno la compilazione.  
  
 Un test più completo potrebbe controllare l'output di questa funzione di test confrontandolo al contenuto noto del file XML di esempio. Ma in questa procedura dettagliata ci si accontenterà di ottenere la compilazione del metodo di test.  
  
### <a name="add-a-text-template-file"></a>Aggiungere un file di modello di testo  
 Aggiungere un file di modello di testo e impostare l'estensione dell'output su ".cs".  
  
##### <a name="to-add-a-text-template-file-to-your-project"></a>Per aggiungere un file di modello di testo al progetto  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, fare clic su **Aggiungi**e quindi su **Nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Modello di testo** dal riquadro **Modelli** .  
  
    > [!NOTE]
    >  Assicurarsi di aggiungere un modello di testo e non un modello di testo pre-elaborato.  
  
3.  Nel file, nella direttiva template, modificare l'attributo `hostspecific` in `true`.  
  
     Questa modifica consentirà al codice del modello di ottenere l'accesso ai servizi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
4.  Nella direttiva di output cambiare l'attributo di estensione in ".cs", in modo che il modello generi un file C#. In un progetto Visual Basic è necessario modificarlo in ".vb".  
  
5.  Salvare il file. In questa fase il file di modello di testo deve contenere le righe seguenti:  
  
    ```  
    <#@ template debug="false" hostspecific="true" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
 .  
  
 Si noti che un file con l'estensione .cs viene visualizzato in Esplora soluzioni come file secondario del file di modello. È possibile vederlo facendo clic su [+] accanto al nome del file di modello. Questo file viene generato dal file di modello quando si salva il file di modello o si allontana lo stato attivo da esso. Il file generato sarà compilato come parte del progetto.  
  
 Per comodità, mentre si sviluppa il file di modello, disporre la finestra del file di modello e quella del file generato l'una accanto all'altra. Ciò consente di vedere immediatamente l'output del modello. Si noterà anche che, quando il modello genera codice C# non valido, gli errori sono mostrati nella finestra dei messaggi d'errore.  
  
 Qualsiasi modifica eseguita direttamente nel file generato andrà persa quando si salva il file di modello. È consigliabile pertanto evitare di modificare il file generato o modificarlo solo per brevi esperimenti. È talvolta utile provare un breve frammento di codice nel file generato, in cui IntelliSense è in esecuzione, e quindi copiarlo nel file di modello.  
  
## <a name="developing-the-text-template"></a>Sviluppare il modello di testo  
 Seguendo i migliori consigli per lo sviluppo Agile, si svilupperà il modello per piccoli passi, eliminando alcuni degli errori a ogni incremento, fino a quando il codice di test non viene compilato ed eseguito correttamente.  
  
### <a name="prototype-the-code-to-be-generated"></a>Creare il prototipo del codice da generare  
 Il codice di test richiede una classe per ogni nodo nel file. Di conseguenza, alcuni degli errori di compilazione verranno risolti aggiungendo queste righe al modello e poi salvandolo:  
  
```  
class Catalog {}   
class Artist {}  
class Song {}  
```  
  
 Questo aiuta a vedere quali elementi sono necessari, ma le dichiarazioni devono essere generate dai tipi di nodo nel file XML di esempio. Eliminare queste righe sperimentali dal modello.  
  
### <a name="generate-application-code-from-the-model-xml-file"></a>Generare il codice dell'applicazione dal file XML del modello  
 Per leggere il file XML e generare le dichiarazioni di classe, sostituire il contenuto del modello con il codice di modello seguente:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#  
 XmlDocument doc = new XmlDocument();  
 // Replace this file path with yours:  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
#>  
  public partial class <#= node.Name #> {}  
<#  
 }  
#>  
```  
  
 Sostituire il percorso del file con il percorso corretto per il progetto.  
  
 Si notino i delimitatori di blocco di codice `<#...#>`. Questi delimitatori racchiudono un frammento di codice di programma che genera il testo. I delimitatori di blocco espressione `<#=...#>` racchiudono un'espressione che può essere valutata in una stringa.  
  
 Quando si scrive un modello che genera codice sorgente per l'applicazione, si ha a che fare con due testi di programma separati. Il programma all'interno dei delimitatori di blocco di codice viene eseguito ogni volta che si salva il modello o si sposta lo stato attivo a un'altra finestra. Il testo generato, che compare fuori dai delimitatori, viene copiato nel file generato e diventa parte del codice dell'applicazione.  
  
 La direttiva `<#@assembly#>` si comporta come un riferimento, rendendo l'assembly disponibile per il codice del modello. L'elenco degli assembly visualizzato dal modello è separato dall'elenco dei riferimenti nel progetto di applicazione.  
  
 La direttiva `<#@import#>` agisce come un'istruzione `using` , consentendo di usare i nomi brevi delle classi nello spazio dei nomi importato.  
  
 Purtroppo, anche se questo modello genera il codice, produce una dichiarazione di classe per ogni nodo del file XML di esempio, perciò, se sono presenti più istanze del nodo `<song>` , vengono visualizzate più dichiarazioni della classe song.  
  
### <a name="read-the-model-file-then-generate-the-code"></a>Leggere il file di modello, quindi generare il codice  
 Molti modelli di testo seguono un pattern in cui la prima parte del modello legge il file di origine e la seconda parte genera il modello. È necessario leggere tutto il file di esempio per riepilogare i tipi di nodo che contiene e quindi generare le dichiarazioni di classe. È necessario un altro `<#@import#>` per poter usare `Dictionary<>:`  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
<#  
 // Read the model file  
 XmlDocument doc = new XmlDocument();  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 Dictionary <string, string> nodeTypes =   
        new Dictionary<string, string>();  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   nodeTypes[node.Name] = "";  
 }  
 // Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= nodeName #> {}  
<#  
 }  
#>  
```  
  
### <a name="add-an-auxiliary-method"></a>Aggiungere un metodo ausiliario  
 Un blocco di controllo della funzionalità di classe è un blocco in cui è possibile definire metodi ausiliari. Il blocco è delimitato da `<#+...#>` e deve essere visualizzato come ultimo blocco del file.  
  
 Se si preferisce che i nomi delle classi inizino con una lettera maiuscola, è possibile sostituire l'ultima parte del modello con il seguente codice di modello:  
  
```  
// Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= UpperInitial(nodeName) #> {}  
<#  
 }  
#>  
<#+  
 private string UpperInitial(string name)  
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }  
#>  
```  
  
 In questa fase il file con estensione .cs generato contiene le seguenti dichiarazioni:  
  
```  
public partial class Catalog {}  
public partial class Artist {}  
public partial class Song {}  
```  
  
 È possibile aggiungere altri dettagli, quali le proprietà per i nodi figlio, attributi e testo interno, mediante lo stesso approccio.  
  
### <a name="accessing-the-visual-studio-api"></a>Accesso all'API di Visual Studio  
 L'impostazione dell'attributo `hostspecific` della direttiva `<#@template#>` consente al modello di ottenere l'accesso all'API [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Il modello può usarla per ottenere il percorso del file di progetto, per evitare di usare un percorso di file assoluto nel codice del modello.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
...  
<#@ assembly name="EnvDTE" #>  
...  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
// Open the prototype document.  
XmlDocument doc = new XmlDocument();  
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
```  
  
## <a name="completing-the-text-template"></a>Completare il modello di testo  
 Il contenuto seguente del modello genera il codice che consente la compilazione e l'esecuzione del codice di test.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{  
<#  
 // Map node name --> child name --> child node type  
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();  
  
 // The Visual Studio host, to get the local file path.  
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
 // Open the prototype document.  
 XmlDocument doc = new XmlDocument();  
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
 // Inspect all the nodes in the document.  
 // The example might contain many nodes of the same type,   
 // so make a dictionary of node types and their children.  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   Dictionary<string, XmlNodeType> subs = null;  
   if (!nodeTypes.TryGetValue(node.Name, out subs))  
   {  
     subs = new Dictionary<string, XmlNodeType>();  
     nodeTypes.Add(node.Name, subs);  
   }  
   foreach (XmlNode child in node.ChildNodes)  
   {  
     subs[child.Name] = child.NodeType;  
   }   
   foreach (XmlNode child in node.Attributes)  
   {  
     subs[child.Name] = child.NodeType;  
   }  
 }  
 // Generate a class for each node type.  
 foreach (string className in nodeTypes.Keys)  
 {  
    // Capitalize the first character of the name.  
#>  
    partial class <#= UpperInitial(className) #>  
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }  
  
<#  
    // Generate a property for each child.  
    foreach (string childName in nodeTypes[className].Keys)  
    {  
      // Allow for different types of child.  
      switch (nodeTypes[className][childName])  
      {  
         // Child nodes:  
         case XmlNodeType.Element:  
#>  
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }  
<#  
         break;  
         // Child attributes:  
         case XmlNodeType.Attribute:  
#>  
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }  
<#  
         break;  
         // Plain text:  
         case XmlNodeType.Text:  
#>  
      public string Text  { get { return thisNode.InnerText; } }  
<#  
         break;  
       } // switch  
     } // foreach class child  
  // End of the generated class:  
#>  
   }   
<#  
 } // foreach class  
  
   // Add a constructor for the root class   
   // that accepts an XML filename.  
   string rootClassName = doc.SelectSingleNode("*").Name;  
#>  
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}  
<#+  
   private string UpperInitial(string name)  
   {  
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);  
   }  
#>  
```  
  
### <a name="running-the-test-program"></a>Esecuzione del programma di test  
 Nel main dell'applicazione console, le righe seguenti eseguiranno il metodo di test. Premere F5 per eseguire il programma in modalità debug:  
  
```  
using System;  
namespace MyProject  
{ class Program  
  { static void Main(string[] args)  
    { new CodeGeneratorTest().TestMethod();  
      // Allow user to see the output:  
      Console.ReadLine();  
} } }  
```  
  
### <a name="writing-and-updating-the-application"></a>Scrittura e aggiornamento dell'applicazione  
 L'applicazione può ora essere scritta in stile fortemente tipizzato, usando le classi generate anziché il codice XML generico.  
  
 Quando lo schema XML cambia, è possibile generare facilmente nuove classi. Il compilatore indicherà allo sviluppatore dove il codice dell'applicazione deve essere aggiornato.  
  
 Per rigenerare le classi quando viene modificato il file XML di esempio, fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni.  
  
## <a name="conclusion"></a>Conclusione  
 Questa procedura dettagliata illustra diverse tecniche e vantaggi della generazione del codice:  
  
-   La*generazione del codice* è la creazione di parte del codice sorgente dell'applicazione da un *modello*. Il modello contiene le informazioni in un formato adatto per il dominio dell'applicazione e può cambiare durante la vita dell'applicazione.  
  
-   La tipizzazione forte è uno dei vantaggi della generazione del codice. Mentre il modello rappresenta le informazioni in un formato più adatto all'utente, il codice generato consente ad altre parti dell'applicazione di gestire le informazioni mediante un set di tipi.  
  
-   IntelliSense e il compilatore consentono di creare codice conforme allo schema del modello, sia quando si scrive nuovo codice che quando lo schema viene aggiornato.  
  
-   L'aggiunta di un singolo file di modello non complicato a un progetto può fornire questi vantaggi.  
  
-   Un modello di testo può essere sviluppato e testato rapidamente e in modo incrementale.  
  
 In questa procedura dettagliata il codice del programma viene effettivamente generato da un'istanza del modello, un esempio rappresentativo dei file XML che l'applicazione elaborerà. In un approccio più formale, lo schema XML sarebbe l'input del modello, nella forma di un file con estensione .xsd o di una definizione di linguaggio specifica del dominio. Tale approccio potrebbe facilitare la determinazione da parte del modello di caratteristiche quali la molteplicità di una relazione.  
  
## <a name="troubleshooting-the-text-template"></a>Risoluzione dei problemi del modello di testo  
 In caso di errori di compilazione o di trasformazione del modello nell'**Elenco errori** o se il file di output non è stato generato correttamente, è possibile risolvere i problemi del modello di testo con le tecniche descritte in [Generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)