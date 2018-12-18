---
title: Personalizzazione di archiviazione di File e la serializzazione XML | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a15a331d465c2450f0f1e6230eac3415106e860b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-file-storage-and-xml-serialization"></a>Personalizzazione dell'archiviazione dei file e della serializzazione XML
Quando l'utente salva un'istanza di, o *modello*, di un linguaggio specifico di dominio (DSL) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], un file XML viene creato o aggiornato. Il file può essere ricaricato per ricreare il modello nell'archivio.  
  
 È possibile personalizzare lo schema di serializzazione modificando le impostazioni in **il comportamento di serializzazione Xml** in Esplora DSL. È presente un nodo in **il comportamento di serializzazione Xml** per ogni classe di dominio, proprietà e relazioni. Le relazioni sono posizionate nelle classi di origine. Esistono anche nodi corrispondenti per la forma connettore e le classi di diagramma.  
  
 È anche possibile scrivere codice programma per la personalizzazione più avanzata.  
  
> [!NOTE]
>  Se si desidera salvare il modello in un formato specifico, ma non è necessario ricaricarlo da tale modulo, considerare l'utilizzo di modelli di testo per generare l'output dal modello, anziché uno schema di serializzazione personalizzata. Per ulteriori informazioni, vedere [la generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>File di modello e diagramma  
 Ogni modello viene in genere salvata in due file:  
  
-   Il file del modello ha un nome, ad esempio **Model1.mydsl**. Archivia gli elementi del modello e le relazioni e le relative proprietà. L'estensione di file, ad esempio **.mydsl** varia a seconda di **FileExtension** proprietà del **Editor** nodo nella definizione DSL.  
  
-   Il file di diagramma ha un nome, ad esempio **Model1.mydsl.diagram**. Archivia le forme, connettori e le relative posizioni, colori, spessori e altri dettagli dell'aspetto del diagramma. Se l'utente elimina un **.diagram** file, le informazioni essenziali nel modello non vengono perse. Solo il layout del diagramma viene perso. Quando viene aperto il file del modello, impostare un valore predefinito di forme e connettori verranno creati.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Per modificare l'estensione di file di un linguaggio DSL  
  
1.  Aprire la definizione DSL. In Esplora DSL, scegliere il nodo Editor.  
  
2.  Nella finestra Proprietà modificare il **FileExtension** proprietà. Non includere iniziale "." dell'estensione di file.  
  
3.  In Esplora soluzioni, modificare il nome dei file di modello di due elementi in **DslPackage\ProjectItemTemplates**. Questi file presentano nomi che seguono questo formato:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>Lo schema di serializzazione predefinito  
 Per creare un esempio di questo argomento, la seguente definizione DSL è stata usata.  
  
 ![Diagramma della definizione DSL &#45; modello di albero genealogico](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Questo linguaggio DSL è stato usato per creare un modello che presenta l'aspetto seguente sullo schermo.  
  
 ![Diagramma dell'albero genealogico e casella degli strumenti Esplora](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Questo modello è stato salvato e quindi nuovamente aperto nell'editor di testo XML:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 Si noti quanto segue sul modello serializzato:  
  
-   Tutti i nodi XML ha un nome che corrisponde al nome della classe un dominio, ad eccezione del fatto che la lettera iniziale è in minuscola. Ad esempio, `familyTreeModel` e `person`.  
  
-   Proprietà di dominio, ad esempio nome e BirthYear vengono serializzate come attributi nei nodi XML. Nuovamente, il carattere iniziale del nome della proprietà viene convertito in caratteri minuscoli.  
  
-   Ogni relazione è serializzato come un nodo XML annidato all'interno della fine dell'origine della relazione. Il nodo ha lo stesso nome della proprietà di ruolo di origine, ma con un carattere iniziale di lettere minuscole.  
  
     Ad esempio, nella definizione del linguaggio DSL, un ruolo denominato **persone** può essere recuperato nel **albero genealogico FamilyTree** classe.  Nel codice XML, questo è rappresentato dal nodo denominato `people` annidato all'interno di `familyTreeModel` nodo.  
  
-   Fine della destinazione di ogni relazione di incorporamento è serializzato come un nodo annidato sotto la relazione. Ad esempio, il `people` nodo contiene numerosi `person` nodi.  
  
-   Fine della destinazione di ogni relazione di riferimento viene serializzato come un *moniker*, che consente di codificare un riferimento all'elemento di destinazione.  
  
     Ad esempio, in un `person` nodo può esistere un `children` relazione. Questo nodo contiene i moniker, ad esempio:  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Informazioni sui moniker  
 Moniker vengono utilizzati per rappresentare i riferimenti incrociati tra le diverse parti dei file di modello e diagramma. Vengono inoltre utilizzati nel `.diagram` file per fare riferimento ai nodi nel file di modello. Esistono due forme del moniker:  
  
-   *Moniker ID* offerta il GUID dell'elemento di destinazione. Ad esempio:  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *Qualificato moniker chiave* identificare l'elemento di destinazione, il valore di una proprietà di dominio designato denominata chiave del moniker. Il moniker dell'elemento di destinazione viene aggiunto come prefisso il moniker del relativo elemento padre nell'albero di relazioni di incorporamento.  
  
     Nell'esempio seguente vengono estratti da un linguaggio DSL in cui vi è una classe di dominio denominata Album, che ha una relazione di incorporamento di un dominio di classe denominato brano:  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     Moniker chiave completo verrà utilizzato se la classe di destinazione dispone di una proprietà di dominio per cui l'opzione **chiave Moniker** è impostato su `true` in **il comportamento di serializzazione Xml**. Nell'esempio, questa opzione è impostata per le proprietà di dominio denominate "Title" nelle classi di dominio "Album" e "Brano".  
  
 Moniker chiave completo sono più facili da leggere rispetto moniker ID. Se si intende il codice XML del file di modello per essere letto da persone, prendere in considerazione l'utilizzo di moniker chiave completo. Tuttavia, è possibile che all'utente di impostare più di un elemento per la stessa chiave moniker. Le chiavi duplicate potrebbe causare il file non di ricaricare correttamente. Pertanto, se si definisce una classe di dominio a cui fa riferimento l'utilizzo di moniker chiave completo, è consigliabile modi per impedire che l'utente salva un file con il moniker duplicato.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Per impostare una classe di dominio moniker ID riferimento  
  
1.  Assicurarsi che **chiave Moniker** è `false` per ogni proprietà del dominio nella classe e le relative classi base.  
  
    1.  In Esplora DSL espandere **dati Behavior\Class di serializzazione Xml\\***\<la classe di dominio >***\Element dati**.  
  
    2.  Verificare che **chiave Moniker** è `false` per ogni proprietà del dominio.  
  
    3.  Se la classe di dominio ha una classe base, ripetere la procedura descritta in tale classe.  
  
2.  Impostare **Id serializzare**  =  `true` per la classe di dominio.  
  
     Questa proprietà è reperibile nella **il comportamento di serializzazione Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Per impostare una classe di dominio completo moniker chiave di riferimento  
  
-   Impostare **chiave Moniker** per una proprietà di dominio di una classe di dominio esistente. Il tipo della proprietà deve essere `string`.  
  
    1.  In Esplora DSL espandere **dati Behavior\Class di serializzazione Xml\\***\<la classe di dominio >***\Element dati**, quindi selezionare la proprietà di dominio.  
  
    2.  Nella finestra Proprietà impostare **chiave Moniker** a `true`.  
  
-   \- oppure -  
  
     Creare una nuova classe di dominio utilizzando il **la classe di dominio denominato** strumento.  
  
     Questo strumento crea una nuova classe che dispone di una proprietà di dominio denominata Name. Il **è il nome di elemento** e **chiave Moniker** le proprietà di questa proprietà di dominio vengono inizializzate `true`.  
  
-   \- oppure -  
  
     Creare una relazione di ereditarietà dalla classe di dominio a un'altra classe che ha una proprietà chiave moniker.  
  
### <a name="avoiding-duplicate-monikers"></a>Evitare i moniker duplicati  
 Se si utilizzano i moniker chiavi completi, è possibile che due elementi nel modello a un utente potrebbero avere lo stesso valore nella proprietà chiave. Ad esempio, se il modello DSL dispone di una persona che ha un nome di proprietà di classe, l'utente può impostare i nomi di due elementi uguali. Sebbene il modello può essere salvata in file, è necessario non ricaricare correttamente.  
  
 Esistono diversi metodi che consentono di evitare questa situazione:  
  
-   Impostare **è il nome di elemento**  =  `true` per la proprietà chiave di dominio. Selezionare la proprietà di dominio del diagramma della definizione DSL e quindi impostare il valore nella finestra Proprietà.  
  
     Quando l'utente crea una nuova istanza della classe, questo valore, la proprietà di dominio venga assegnato automaticamente un valore diverso. Il comportamento predefinito viene aggiunto un numero alla fine del nome della classe. Questo non impedisce all'utente di modifica del nome di un duplicato, ma è utile nel caso quando l'utente non imposta il valore prima di salvare il modello.  
  
-   Abilitare la convalida per il linguaggio DSL. In Esplora DSL, selezionare Editor\Validation e impostare il **utilizza...**  proprietà `true`.  
  
     È un metodo di convalida generato automaticamente che controlla per ambiguità. Il metodo è incluso il `Load` categoria di convalida. Ciò assicura che l'utente verrà avvisato che potrebbe non essere possibile riaprire il file.  
  
     Per ulteriori informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>I qualificatori e moniker percorsi  
 Un moniker di chiave completo termina con la chiave di moniker ed è il prefisso con il moniker dell'elemento padre dell'albero di incorporamento. Ad esempio, se il moniker dell'Album è:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 Uno di brani in Album potrebbe quindi essere:  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 Tuttavia, se album fanno riferimento invece ID, il moniker sarà come segue:  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Si noti che poiché un GUID è univoco, che non è mai preceduto dal moniker del relativo padre.  
  
 Se si sa che una proprietà di un dominio particolare avrà sempre un valore univoco all'interno di un modello, è possibile impostare **è qualificatore Moniker** a `true` per tale proprietà. In questo modo, potrà essere utilizzato come qualificatore, senza usare il moniker dell'elemento padre. Ad esempio, se si impostano entrambe **è qualificatore Moniker** e **chiave Moniker** per la proprietà del dominio titolo della classe Album nome o l'identificatore del modello non viene usato nel moniker per Album e il relativo incorporato elementi figlio:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>La struttura del codice XML di personalizzazione  
 Per apportare le seguenti personalizzazioni, espandere il **il comportamento di serializzazione Xml** nodo in Esplora DSL. In una classe di dominio, espandere il nodo dell'elemento dati per visualizzare l'elenco di proprietà e relazioni vengono originate in questa classe. Selezionare una relazione e modificare le opzioni nella finestra Proprietà.  
  
-   Impostare **elemento omettere** su true per omettere il nodo di ruolo di origine, mantenendo solo l'elenco di elementi di destinazione. Non impostare questa opzione se non esiste più di una relazione tra le classi di origine e di destinazione.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   Impostare **modulo completo utilizzo** per incorporare i nodi di destinazione nei nodi che rappresentano le istanze della relazione. Questa opzione viene impostata automaticamente quando si aggiunge le proprietà del dominio a una relazione di dominio.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   Impostare **rappresentazione** = **elemento** disponga di una proprietà dominio salvata come elemento anziché come valori di attributo.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   Per modificare l'ordine in cui vengono serializzate gli attributi e relazioni, fare doppio clic su un elemento sotto l'elemento dati e utilizzare il **Sposta su** o **Sposta giù** i comandi di menu.  
  
## <a name="major-customization-using-program-code"></a>Personalizzazione principale tramite il codice di programma  
 È possibile sostituire parti o tutti gli algoritmi di serializzazione.  
  
 È consigliabile esaminare il codice in **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Per personalizzare la serializzazione di una determinata classe  
  
1.  Impostare **personalizzato è** nel nodo per tale classe in **il comportamento di serializzazione Xml**.  
  
2.  Trasforma tutti i modelli, compilare la soluzione e analizzare gli errori di compilazione risultante. Commenti quasi ogni errore spiegano il codice è necessario fornire.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Per fornire la serializzazione personalizzata per l'intero modello  
  
1.  Eseguire l'override di metodi in Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Opzioni di comportamento di serializzazione Xml  
 In Esplora DSL, il nodo di comportamento di serializzazione Xml contiene un nodo figlio per ogni dominio classe relazione, forma, connettore e Diagramma classe. In ciascuno di questi nodi è un elenco di proprietà e relazioni originate questo elemento. Le relazioni sono rappresentate nella propria destra e sotto le classi di origine.  
  
 Nella tabella seguente vengono riepilogate le opzioni che è possibile impostare in questa sezione della definizione DSL. In ogni caso, selezionare un elemento in Esplora DSL e impostare le opzioni nella finestra Proprietà.  
  
### <a name="xml-class-data"></a>Dati XML (classe)  
 Questi elementi sono contenuti in Esplora DSL **dati Behavior\Class di serializzazione Xml**.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|Dispone di Schema dell'elemento personalizzato|Se True, indica che la classe di dominio ha uno schema di elemento personalizzato|  
|È personalizzato|Impostare questa proprietà su **True** se si desidera scrivere codice di serializzazione e deserializzazione per questa classe di dominio.<br /><br /> Compilare la soluzione, esaminare gli errori per individuare le istruzioni dettagliate.|  
|Classe di dominio|Classe di dominio a cui si applica questo nodo di dati della classe. Sola lettura.|  
|Nome elemento|Nome del nodo XML per gli elementi di questa classe. Il valore predefinito è una versione minuscola del nome della classe di dominio.|  
|Nome dell'attributo moniker|Nome dell'attributo utilizzato negli elementi moniker per contenere il riferimento. Se è vuota, viene utilizzato il nome della proprietà chiave o id.<br /><br /> In questo esempio è "name":`<personMoniker name="/Mike Nash"/>`|  
|Nome dell'elemento moniker|Nome dell'elemento xml utilizzato per i moniker che fanno riferimento agli elementi di questa classe.<br /><br /> Il valore predefinito è una versione minuscola del nome della classe aggiunto il suffisso "Moniker". Ad esempio `personMoniker`.|  
|Nome del tipo moniker|Nome del tipo xsd generato per i moniker agli elementi di questa classe. Lo schema XSD è **Dsl\Generated codice\\\*Schema.xsd**|  
|Serializzare Id|Se True, il GUID elemento è incluso nel file. Deve essere true se è presente alcuna proprietà che è contrassegnato come **chiave Moniker** e DSL definisce relazioni di riferimento di questa classe.|  
|Nome tipo|Nome del tipo xml generato nel xsd dalla classe di dominio designato.|  
|Note|Informale note associate a questo elemento|  
  
### <a name="xml-property-data"></a>Dati di proprietà XML  
 I nodi di proprietà XML si trovano sotto i nodi della classe.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|Proprietà del dominio|Proprietà a cui si applicano i dati di configurazione di serializzazione xml. Sola lettura.|  
|Moniker chiave|Se True, la proprietà viene utilizzata come chiave per la creazione di moniker che fanno riferimento a istanze di questa classe di dominio.|  
|Moniker qualificatore|Se True, la proprietà viene utilizzata per creare il qualificatore in moniker. Se è false e SerializeId non vale per questa classe di dominio, i moniker vengono qualificati dal moniker dell'elemento padre dell'albero di incorporamento.|  
|Rappresentazione|Se l'attributo, la proprietà viene serializzato come un attributo xml. Se l'elemento è serializzato come elemento. Se Ignora, non è serializzato.|  
|Nome XML|Nome utilizzato per l'elemento che rappresenta la proprietà o un attributo xml. Per impostazione predefinita, questa è una versione minuscola del nome di proprietà del dominio.|  
|Note|Informale note associate a questo elemento|  
  
### <a name="xml-role-data"></a>Dati XML ruolo  
 I nodi ruolo dati si trovano in nodi di classe di origine.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|È un Moniker personalizzato|Impostare su true se si desidera fornire codice personalizzato per la generazione e la risoluzione moniker che passano attraverso questa relazione.<br /><br /> Per istruzioni dettagliate, compilare la soluzione e quindi fare doppio clic sui messaggi di errore.|  
|Relazione di dominio|Specifica la relazione in cui queste opzioni si applicano. Sola lettura.|  
|Omettere l'elemento|Se true, il nodo XML che corrisponde al ruolo di origine viene omesso dallo schema.<br /><br /> Se non esiste più di una relazione tra le classi di origine e di destinazione, il nodo di ruolo viene fatta distinzione tra i collegamenti che appartengono a due relazioni. È pertanto consigliabile non impostare questa opzione in questo caso.|  
|Nome dell'elemento ruolo|Specifica il nome dell'elemento XML che è derivato dal ruolo di origine. Il valore predefinito è il nome di proprietà del ruolo.|  
|Utilizzare il modulo completo|Se true, ogni elemento di destinazione o un moniker è racchiuso in un nodo XML che rappresenta la relazione. Questo deve essere impostato su true se la relazione presenta una proprietà dominio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)