---
title: Linee guida per la scrittura di modelli di testo T4 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: accf32ad313cbbfe11c2e85fdfe3101ab428c4a4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Linee guida per la scrittura di modelli di testo T4
Queste linee guida generali potrebbero essere utile se si sta generando codice programma o altre risorse dell'applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le regole non sono fisse.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Linee guida per i modelli T4 in fase di progettazione  
 Modelli T4 in fase di progettazione sono modelli che generano il codice del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto in fase di progettazione. Per ulteriori informazioni, vedere [generazione codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Generare aspetti variabili dell'applicazione.  
 Generazione di codice è particolarmente utile per gli aspetti dell'applicazione che potrebbero cambiare nel corso del progetto, o cambia tra le diverse versioni dell'applicazione. Gli aspetti più invarianti farne questi aspetti variabili in modo che è possibile stabilire più facilmente ciò che deve essere generato. Ad esempio, se l'applicazione fornisce un sito Web, separare la pagina standard serve funzioni dalla logica che definisce i percorsi di navigazione da una pagina a un altro.  
  
 Codificare gli aspetti variabili in uno o più modelli di origine.  
 Un modello è un file o database che legge ogni modello per ottenere i valori specifici per parti variabili del codice che deve essere generato. I modelli possono essere database, file XML di progettazione, diagrammi o linguaggi specifici di dominio. In genere, un modello viene utilizzato per generare molti file in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Ogni file è generato da un modello distinto.  
  
 È possibile utilizzare più di un modello in un progetto. Ad esempio, è possibile definire un modello per la navigazione tra pagine Web e un modello distinto per il layout delle pagine.  
  
 Concentrare il modello a vocabolario e le esigenze degli utenti, non l'implementazione.  
 Ad esempio, in un'applicazione del sito Web, è previsto il modello per fare riferimento a pagine Web e i collegamenti ipertestuali.  
  
 Idealmente, scegliere un formato di presentazione che si adatta al tipo di informazioni che rappresenta il modello. Ad esempio, un modello di percorsi di navigazione tramite un sito Web potrebbe essere un diagramma di finestre e frecce.  
  
 Testare il codice generato.  
 Utilizzare i test manuali o automatizzati per verificare che il codice risultante funzioni come gli utenti richiedono. Evitare di generare test dallo stesso modello da cui viene generato il codice.  
  
 In alcuni casi, test generici possono essere eseguite direttamente sul modello. Ad esempio, è possibile scrivere un test che assicura che ogni pagina del sito Web sia raggiungibile tramite navigazione da un altro.  
  
 Consenti per codice personalizzato: generare classi parziali.  
 Consenti per il codice scritto manualmente inoltre per il codice generato. È insolito per uno schema di generazione di codice in grado di account per tutte le possibili varianti che potrebbero verificarsi. Pertanto, si dovrebbero aggiungere o modificare parte del codice generato. In cui il materiale generato è in un linguaggio .NET, ad esempio [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], due strategie sono particolarmente utili:  
  
-   Le classi generate devono essere parziali. In questo modo è possibile aggiungere contenuto al codice generato.  
  
-   Le classi devono essere generate in coppie, una eredita da altra. La classe di base deve contenere tutti i metodi generati e le proprietà e la classe derivata deve contenere solo i costruttori. In questo modo il codice scritto a mano eseguire l'override di uno dei metodi generati.  
  
 In altri linguaggi generati, ad esempio XML, utilizzare il `<#@include#>` direttiva per creare semplici combinazioni del contenuto generato e scritta manualmente. Nei casi più complessi, potrebbe essere necessario scrivere un passaggio di post-elaborazione che combina il file generato con tutti i file scritti a mano.  
  
 Spostare il materiale comune in file di inclusione o modelli in fase di esecuzione  
 Per evitare la ripetizione simile blocchi di testo e il codice in più modelli, utilizzare il `<#@ include #>` direttiva. Per ulteriori informazioni, vedere [direttiva Include T4](../modeling/t4-include-directive.md).  
  
 È possibile anche creare modelli di testo in fase di esecuzione in un progetto separato e quindi chiamarle dal modello di progettazione. A tale scopo, utilizzare il `<#@ assembly #>` direttiva per l'accesso al progetto separato. Per esempi, vedere ["Ereditarietà in modelli di testo" nel Blog degli Mathew](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Provare a spostare grandi blocchi di codice in un assembly separato.  
 Se si dispone di blocchi di codice di grandi dimensioni e i blocchi della funzionalità di classe, potrebbe essere utile spostare alcuni questo codice in metodi che vengono compilati in un progetto separato. È possibile utilizzare il `<#@ assembly #>` direttiva per accedere al codice nel modello. Per ulteriori informazioni, vedere [direttiva Assembly T4](../modeling/t4-assembly-directive.md).  
  
 È possibile inserire i metodi in una classe astratta che può ereditare il modello. La classe astratta deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Per ulteriori informazioni, vedere [direttiva Template T4](../modeling/t4-template-directive.md).  
  
 Generare il codice, non i file di configurazione  
 Un metodo di creazione di un'applicazione variabile consiste nello scrivere codice programma generico che accetta un file di configurazione. Un'applicazione scritta in questo modo è molto flessibile e può essere riconfigurata quando cambiano i requisiti di business, senza ricompilare l'applicazione. Tuttavia, uno svantaggio di questo approccio è che l'applicazione eseguirà inferiori rispetto a un'applicazione più specifica. Inoltre, il codice programma sarà più difficile da leggere e gestire, in parte perché per gestire i tipi più generici deve sempre.  
  
 Al contrario, un'applicazione vengono generate le cui parti variabili prima della compilazione può essere fortemente tipizzata. Questo rende molto più semplice e affidabile per scrivere codice scritto a mano e integrarlo con generato parti del software.  
  
 Per ottenere i massimi vantaggi della generazione del codice, provare a generare codice programma anziché i file di configurazione.  
  
 Utilizzare una cartella del codice generato  
 Inserire i modelli e i file generati in una cartella di progetto denominata **codice generato**per renderlo deselezionare che questi non sono file che devono essere modificati direttamente. Se si crea il codice personalizzato per eseguire l'override o aggiungere le classi generate, posizionare queste classi in una cartella denominata **codice personalizzato**. La struttura di un progetto tipico è simile al seguente:  
  
```  
MyProject  
   Custom Code  
      Class1.cs  
      Class2.cs  
   Generated Code  
      Class1.tt  
          Class1.cs  
      Class2.tt  
          Class2.cs  
   AnotherClass.cs  
  
```  
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Linee guida per i modelli T4 (pre-elaborato) della fase di esecuzione  
 Spostare il materiale comune nei modelli ereditati  
 È possibile utilizzare l'ereditarietà per condividere i metodi e i blocchi di testo tra i modelli di testo T4. Per ulteriori informazioni, vedere [direttiva Template T4](../modeling/t4-template-directive.md).  
  
 È inoltre possibile utilizzare file di inclusione che dispongono di modelli in fase di esecuzione.  
  
 Spostare grandi quantità di codice in una classe parziale.  
 Ogni modello in fase di esecuzione genera una definizione di classe parziale che include lo stesso nome del modello. È possibile scrivere un file di codice che contiene un'altra definizione parziale della stessa classe. È possibile aggiungere i costruttori, campi e metodi alla classe in questo modo. Questi membri possono essere chiamati dai blocchi di codice nel modello.  
  
 Un vantaggio di questa operazione è che il codice è più facile da scrivere, perché IntelliSense è disponibile. Inoltre, è possibile ottenere una migliore separazione tra la presentazione e la logica sottostante.  
  
 Ad esempio, in **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 In **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Consenti per codice personalizzato: fornire punti di estensione  
 Si consiglia di generare metodi virtuali in \<funzionalità di classe #+ blocchi #>. In questo modo un singolo modello da utilizzare in molti contesti senza alcuna modifica. Anziché modificare il modello, è possibile creare una classe derivata che fornisce la logica aggiuntiva minima. La classe derivata può essere codice normale, o può essere un modello in fase di esecuzione.  
  
 Ad esempio, in MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 Nel codice di un'applicazione:  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>Linee guida per tutti i modelli T4  
 Raccolta di dati separata dalla generazione di testo  
 Tentare di evitare la combinazione di calcolo e blocchi di testo. In ogni modello di testo, utilizzare il primo \<blocco # # > per impostare le variabili ed eseguire calcoli complessi. Dal primo blocco di testo fino alla fine del modello o il primo \<funzionalità di classe #+ blocco #>, evitare espressioni lunghe ed evitare cicli e istruzioni condizionali, a meno che non contengono blocchi di testo. Questa pratica rende più facile da leggere e gestire il modello.  
  
 Non utilizzare `.tt` i file di inclusione  
 Utilizzare un'estensione di file diverso, ad esempio `.ttinclude` i file di inclusione. Utilizzare `.tt` solo per i file che si desidera essere elaborate in fase di esecuzione o in fase di progettazione modelli di testo. In alcuni casi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] riconosce `.tt` file e di impostare automaticamente le relative proprietà per l'elaborazione.  
  
 Avviare ogni modello come prototipo fisso.  
 Scrivere un esempio di codice o del testo che si desidera generare e verificare che sia corretto. Impostare la relativa estensione tt e inserire gradualmente il codice che modifica il contenuto mediante la lettura del modello.  
  
 È possibile utilizzare modelli tipizzati.  
 Sebbene sia possibile creare uno schema XML o di database per i modelli, potrebbe essere utile creare un linguaggio specifico di dominio (DSL). Un linguaggio DSL presenta il vantaggio che genera una classe per rappresentare ogni nodo nello schema e le proprietà per rappresentare gli attributi. Ciò significa che è possibile programmare in termini di modello di business. Ad esempio:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 È consigliabile utilizzare i diagrammi per i modelli.  
 Molti modelli in modo più efficace vengono presentati e gestiti semplicemente come tabelle di testo, specialmente se sono molto grandi.  
  
 Tuttavia, per alcuni tipi di requisiti aziendali, è importante chiarire set complessi di relazioni e flussi di lavoro e i diagrammi sono il mezzo meglio indicato. Un vantaggio di un diagramma è che è facile discutere con gli utenti e altre parti interessate. Generazione di codice da un modello di livello dei requisiti aziendali, rendere il codice più flessibile quando cambiano i requisiti.  
  
 È inoltre possibile progettare un nuovo tipo di diagramma come un linguaggio specifico di dominio (DSL). Codice può essere generato da UML e DSL. Per ulteriori informazioni, vedere [analisi e modellazione architettura](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
