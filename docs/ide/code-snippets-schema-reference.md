---
title: Riferimento dello schema dei frammenti di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c267b110b67a69b526bb7efc985bb22bb954b3a1
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="code-snippets-schema-reference"></a>Riferimento dello schema dei frammenti di codice
I frammenti di codice IntelliSense sono parti di codice già create e pronte per essere inserite nell'applicazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Questi frammenti di codice consentono di incrementare la produttività riducendo la quantità di tempo dedicata alla digitazione di codice ripetitivo o alla ricerca di esempi. È possibile usare l'XML Schema dei frammenti di codice IntelliSense per creare frammenti di codice personali e aggiungerli ai frammenti di codice già inclusi in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="intellisense-code-snippets-schema-elements"></a>Elementi dello schema dei frammenti di codice IntelliSense  
  
||||  
|-|-|-|  
|[Elemento Assembly](../ide/code-snippets-schema-reference.md#assembly)|[Elemento HelpUrl](../ide/code-snippets-schema-reference.md#helpurl)|[Elemento References](../ide/code-snippets-schema-reference.md#references)|  
|[Elemento Author](../ide/code-snippets-schema-reference.md#author)|[Elemento ID](../ide/code-snippets-schema-reference.md#id)|[Elemento Shortcut](../ide/code-snippets-schema-reference.md#shortcut)|  
|[Elemento Code](../ide/code-snippets-schema-reference.md#code)|[Elemento Import](../ide/code-snippets-schema-reference.md#import)|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|  
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet)|[Elemento Imports](../ide/code-snippets-schema-reference.md#imports)|[Elemento SnippetType](../ide/code-snippets-schema-reference.md#snippettype)|  
|[Elemento CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets)|[Elemento Keyword](../ide/code-snippets-schema-reference.md#keyword)|[Elemento SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes)|  
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations)|[Elemento Keywords](../ide/code-snippets-schema-reference.md#keywords)|[Elemento Title](../ide/code-snippets-schema-reference.md#title)|  
|[Elemento Default](../ide/code-snippets-schema-reference.md#default)|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|[Elemento ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|  
|[Elemento Description](../ide/code-snippets-schema-reference.md#description)|[Elemento Namespace](../ide/code-snippets-schema-reference.md#namespace)|[Elemento Type](../ide/code-snippets-schema-reference.md#type)|  
|[Elemento Function](../ide/code-snippets-schema-reference.md#function)|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|[Elemento Url](../ide/code-snippets-schema-reference.md#url)|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference)||  
  
##  <a name="assembly"></a> Elemento Assembly  
 Specifica il nome dell'assembly a cui fa riferimento il frammento di codice.
  
 Il valore di testo dell'elemento **Assembly** è il nome descrittivo dell'assembly, ad esempio `System.dll` o il nome sicuro, come `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.  
  
```xml  
<Assembly>  
    AssemblyName  
</Assembly>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference)|Contiene informazioni sui riferimenti di assembly richiesti dal frammento di codice.|  
  
 È necessario specificare un valore di testo. Tale testo specifica l'assembly a cui fa riferimento il frammento di codice.  
  
##  <a name="author"></a> Elemento Author  
 Specifica il nome dell'autore del frammento di codice. In **Gestione frammenti di codice** viene visualizzato il nome archiviato nell'elemento `Author` del frammento di codice.  
  
```xml  
<Author>  
   Code Snippet Author  
</Author>    
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Contiene informazioni generali sul frammento di codice.|  
  
 È necessario specificare un valore di testo. Questo testo specifica l'autore del frammento di codice.  
  
## <a name="a-namecode--code-element"></a><a name="code" /> Elemento Code  
Fornisce un contenitore per i blocchi di codice.  
  
### <a name="keywords"></a>Parole chiave
Sono disponibili due parole riservate da usare nel testo dell'elemento `Code`: `$end$` e `$selected$`. `$end$` contrassegna il punto in cui posizionare il cursore dopo l'inserimento del frammento di codice. `$selected$` rappresenta il testo selezionato nel documento da inserire nel frammento di codice quando viene chiamato. Ad esempio, se si avesse:  
  
```  
$selected$ is a great color.  
```  
  
e fosse stata selezionata la parola "Blue" al momento della chiamata al modello, si otterrebbe:  
  
```  
Blue is a great color.  
```  
  
Non è possibile usare `$end$` o `$selected$` più di una volta in un frammento di codice. Se lo si fa, viene riconosciuta solo la seconda istanza. Se si avesse:  
  
```  
$selected$ is a great color. I love $selected$.  
```  
  
e fosse stata selezionata la parola "Blue", si otterrebbe:  
  
```  
 is a great color. I love Blue.  
```  
  
Lo spazio iniziale viene visualizzato perché c'è uno spazio tra `$selected$` e `is`.  
  
Tutte le altre parole chiave `$` vengono definite in modo dinamico nei tag `<Literal>` e `<Object>`.  

Di seguito è riportata la struttura dell'elemento Code:
  
```xml  
<Code Language="Language"  
    Kind="method body/method decl/type decl/page/file/any"  
    Delimiter="Delimiter">  
    Code to insert  
</Code>  
```

È necessario specificare un valore di testo. Il testo specifica il codice, insieme ai valori letterali e agli oggetti, che è possibile usare in caso di inserimento di questo frammento di codice in un file di codice.  

### <a name="attributes"></a>Attributi
Sono disponibili tre attributi per l'elemento Code:

- L'attributo **Language** - _(obbligatorio)_ specifica il linguaggio del frammento di codice. Il valore può essere uno dei seguenti:

   |Valore|Descrizione|  
   |-----|-----------|  
   |`VB`|Identifica un frammento di codice di Visual Basic.|  
   |`CSharp`|Identifica un frammento di codice di C#.|  
   |`CPP`|Identifica un frammento di codice di C++.|  
   |`XML`|Identifica un frammento di codice XML.|  
   |`JavaScript`|Identifica un frammento di codice di JavaScript.|  
   |`SQL`|Identifica un frammento di codice SQL.|  
   |`HTML`|Identifica un frammento di codice HTML.|
 
- L'attributo **Kind** - _(facoltativo)_ specifica il tipo di codice contenuto nel frammento e la posizione in cui un frammento di codice deve essere inserito per la relativa compilazione. Il valore può essere uno dei seguenti:

   |Valore|Descrizione|  
   |-----|-----------|  
   |`method body`|Specifica che il frammento di codice è il corpo di un metodo e deve pertanto essere inserito all'interno di una dichiarazione di metodo.|  
   |`method decl`|Specifica che il frammento di codice è un metodo e deve pertanto essere inserito all'interno di una classe o un modulo.|  
   |`type decl`|Specifica che il frammento di codice è un tipo e deve pertanto essere inserito all'interno di una classe, un modulo o uno spazio dei nomi.|  
   |`file`|Specifica che il frammento di codice è un file di codice completo. Questi frammenti di codice possono essere inseriti autonomamente in un file di codice o all'interno di uno spazio dei nomi.|  
   |`any`|Specifica che il frammento può essere inserito in qualsiasi posizione. Questo tag viene usato per frammenti di codice indipendenti dal contesto, ad esempio i commenti.|

- L'attributo **Delimiter** - _(facoltativo)_ specifica il delimitatore usato per descrivere i valori letterali e gli oggetti nel codice. Per impostazione predefinita, il delimitatore è `$`.

### <a name="parent-element"></a>Elemento padre
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contiene i riferimenti, le importazioni, le dichiarazioni e il codice del frammento di codice.|
  
##  <a name="codesnippet"></a> Elemento CodeSnippet  
 Consente di specificare un'intestazione e più frammenti di codice IntelliSense, che è possibile inserire in file di codice di Visual Studio.  
  
```xml  
<CodeSnippet Format="x.x.x">  
    <Header>... </Header>  
    <Snippet>... </Snippet>  
</CodeSnippet>  
```  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Format`|Attributo obbligatorio. Specifica la versione dello schema del frammento di codice. L'attributo Format deve essere una stringa con sintassi x.x.x, dove ogni "x" rappresenta un valore numerico del numero di versione. In Visual Studio saranno ignorati i frammenti di codice con attributi `Format` incomprensibili al programma.|  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Elemento obbligatorio. Contiene informazioni generali sul frammento di codice. In un frammento di codice deve essere presente esattamente un elemento `Header`.|  
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|Elemento obbligatorio. Contiene il codice che verrà inserito da Visual Studio. In un frammento di codice deve essere presente esattamente un elemento `Snippet`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets)|Elemento radice dell'XML Schema dei frammenti di codice.|  
  
##  <a name="codesnippets"></a> Elemento CodeSnippets  
 Raggruppa gli elementi [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet). L'elemento `CodeSnippets` è l'elemento radice dell'XML Schema dei frammenti di codice.  
  
```xml  
<CodeSnippets>  
    <CodeSnippet>... </CodeSnippet>  
</CodeSnippets>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet)|Elemento facoltativo. Elemento padre di tutti i dati del frammento di codice. Possono esistere zero o più elementi `CodeSnippet` in un elemento `CodeSnippets`.|  
  
##  <a name="declarations"></a> Elemento Declarations  
 Specifica i valori letterali e gli oggetti che costituiscono le parti modificabili di un frammento di codice.  
  
```xml  
<Declarations>  
    <Literal>... </Literal>  
    <Object>... </Object>  
</Declarations>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|Elemento facoltativo. Definisce i valori letterali modificabili del frammento di codice. Possono esistere zero o più elementi `Literal` in un elemento `Declarations`.|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Elemento facoltativo. Definisce gli oggetti modificabili del frammento di codice. Possono esistere zero o più elementi `Object` in un elemento `Declarations`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contiene i riferimenti, le importazioni, le dichiarazioni e il codice del frammento di codice.|  
  
##  <a name="default"></a> Elemento Default  
 Specifica il valore predefinito del valore letterale o dell'oggetto di un frammento di codice IntelliSense.  
  
```xml  
<Default>  
    Default value  
</Default>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|Definisce i campi con valore letterale del frammento di codice che è possibile modificare.|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Definisce i campi di oggetti del frammento di codice che è possibile modificare.|  
  
 È necessario specificare un valore di testo. Il testo specifica l'impostazione predefinita del valore letterale o dell'oggetto che popola i campi modificabili del frammento di codice.  
  
##  <a name="description"></a> Elemento Description  
 Specifica informazioni descrittive sul contenuto di un frammento di codice IntelliSense.  
  
```xml  
<Description>  
    Code Snippet Description  
</Description>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Contiene informazioni generali sul frammento di codice.|  
  
 È necessario specificare un valore di testo. Questo testo descrive il frammento di codice.  
  
##  <a name="function"></a> Elemento Function  
 Specifica una funzione da eseguire quando il valore letterale o l'oggetto ricevono lo stato attivo in Visual Studio.  
  
> [!NOTE]
>  L'elemento `Function` è supportato solo nei frammenti di codice di C#.  
  
```xml  
<Function>  
    FunctionName  
</Function>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|Definisce i campi con valore letterale del frammento di codice che è possibile modificare.|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Definisce i campi di oggetti del frammento di codice che è possibile modificare.|  
  
 È necessario specificare un valore di testo. Questo testo specifica una funzione da eseguire quando il campo con valore letterale o con oggetto riceve lo stato attivo in Visual Studio.  
  
##  <a name="header"></a> Elemento Header  
 Specifica informazioni generali sul frammento di codice IntelliSense.  
  
```xml  
<Header>  
    <Title>... </Title>  
    <Author>... </Author>  
    <Description>... </Description>  
    <HelpUrl>... </HelpUrl>  
    <SnippetTypes>... </SnippetTypes>  
    <Keywords>... </Keywords>  
    <Shortcut>... </Shortcut>  
</Header>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Author](../ide/code-snippets-schema-reference.md#author)|Elemento facoltativo. Nome della persona o della società che ha creato il frammento di codice. In un elemento `Author` possono essere presenti zero elementi `Header` oppure uno.|  
|[Elemento Description](../ide/code-snippets-schema-reference.md#description)|Elemento facoltativo. Descrizione del frammento di codice. In un elemento `Description` possono essere presenti zero elementi `Header` oppure uno.|  
|[Elemento HelpUrl](../ide/code-snippets-schema-reference.md#helpurl)|Elemento facoltativo. URL contenente altre informazioni sul frammento di codice. In un elemento Header possono essere presenti zero elementi `HelpURL` o uno. **Nota:** in Visual Studio l'elemento `HelpUrl` non viene usato. L'elemento fa parte dell'XML Schema dei frammenti di codice IntelliSense e ogni frammento di codice che contiene l'elemento verrà convalidato, anche se il valore dell'elemento non verrà mai usato.|  
|[Elemento Keywords](../ide/code-snippets-schema-reference.md#keywords)|Elemento facoltativo. Raggruppa gli elementi `Keyword`. In un elemento `Keywords` possono essere presenti zero elementi `Header` oppure uno.|  
|[Elemento Shortcut](../ide/code-snippets-schema-reference.md#shortcut)|Elemento facoltativo. Specifica il testo di collegamento che può essere usato per inserire il frammento. In un elemento `Shortcut` possono essere presenti zero elementi `Header` oppure uno.|  
|[Elemento SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes)|Elemento facoltativo. Raggruppa gli elementi `SnippetType`. In un elemento `SnippetTypes` possono essere presenti zero elementi `Header` oppure uno. In assenza di elementi `SnippetTypes`, il frammento di codice è sempre valido.|  
|[Elemento Title](../ide/code-snippets-schema-reference.md#title)|Elemento obbligatorio. Nome descrittivo del frammento di codice. In un elemento `Title` deve essere presente esattamente un elemento `Header`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet)|Elemento padre di tutti i dati del frammento di codice.|  
  
##  <a name="helpurl"></a> Elemento HelpUrl  
 Specifica un URL nel quale sono presenti altre informazioni su un frammento di codice.  
  
> [!NOTE]
>  In Visual Studio l'elemento `HelpUrl` non viene usato. L'elemento fa parte dell'XML Schema dei frammenti di codice IntelliSense e ogni frammento di codice che contiene l'elemento verrà convalidato, anche se il valore dell'elemento non verrà mai usato.  
  
```xml  
<HelpUrl>  
    www.microsoft.com  
</HelpUrl>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Contiene informazioni generali sul frammento di codice.|  
  
 Il valore di testo è facoltativo. Tale testo specifica l'URL da visitare per ottenere altre informazioni su un frammento di codice.  
  
##  <a name="id"></a> Elemento ID  
 Specifica un identificatore univoco per un elemento `Literal` o `Object`. Due valori letterali o oggetti nello stesso frammento di codice non possono avere lo stesso valore di testo negli elementi `ID`. I valori letterali e gli oggetti non possono contenere un elemento `ID` con un valore end. `$end$` è un valore riservato e viene usato per contrassegnare il punto in cui posizionare il cursore dopo l'inserimento del frammento di codice.  
  
```xml  
<ID>  
    Unique Identifier  
</ID>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|Definisce i campi con valore letterale del frammento di codice che è possibile modificare.|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Definisce i campi di oggetti del frammento di codice che è possibile modificare.|  
  
 È necessario specificare un valore di testo. Tale testo specifica l'identificatore univoco per l'oggetto o il valore letterale.  
  
##  <a name="import"></a> Elemento Import  
 Specifica gli spazi dei nomi importati usati da un frammento di codice IntelliSense.  
  
> [!NOTE]
>  L'elemento `Import` è supportato solo per i progetti di Visual Basic.  
  
```xml  
<Import>  
    <Namespace>... </Namespace>  
</Import>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Namespace](../ide/code-snippets-schema-reference.md#namespace)|Elemento obbligatorio. Specifica lo spazio dei nomi usato dal frammento di codice. In un elemento `Namespace` deve essere presente esattamente un elemento `Import`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Imports](../ide/code-snippets-schema-reference.md#imports)|Elemento di raggruppamento per elementi **Import**.|  
  
##  <a name="imports"></a> Elemento Imports  
 Raggruppa singoli elementi `Import`.  
  
> [!NOTE]
>  L'elemento `Imports` è supportato solo per i progetti di Visual Basic.  
  
```xml  
<Imports>  
    <Import>... </Import>  
<Imports>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Import](../ide/code-snippets-schema-reference.md#import)|Elemento facoltativo. Contiene gli spazi dei nomi importati per il frammento di codice. Possono esistere zero o più elementi **Import** in un elemento `Imports`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contiene i riferimenti, le importazioni, le dichiarazioni e il codice del frammento di codice.|  
  
##  <a name="keyword"></a> Elemento Keyword  
 Specifica una parola chiave personalizzata per il frammento di codice. Le parole chiave del frammento di codice sono usate da Visual Studio e costituiscono un modo standard dei provider di contenuti online di aggiungere parole chiave personalizzate per la ricerca o la classificazione in categorie.  
  
```xml  
<Keyword>  
    Code Snippet Keyword  
</Keyword>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Keywords](../ide/code-snippets-schema-reference.md#keywords)|Raggruppa singoli elementi `Keyword`.|  
  
 È necessario specificare un valore di testo. Parola chiave per il frammento di codice.  
  
##  <a name="keywords"></a> Elemento Keywords  
 Raggruppa singoli elementi `Keyword`. Le parole chiave del frammento di codice sono usate da Visual Studio e costituiscono un modo standard dei provider di contenuti online di aggiungere parole chiave personalizzate per la ricerca o la classificazione in categorie  
  
```xml  
<Keywords>  
    <Keyword>... </Keyword>  
    <Keyword>... </Keyword>  
<Keywords>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Keyword](../ide/code-snippets-schema-reference.md#keyword)|Elemento facoltativo. Contiene singole parole chiave per il frammento di codice. Possono esistere zero o più elementi `Keyword` in un elemento `Keywords`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Contiene informazioni generali sul frammento di codice.|  
  
##  <a name="literal"></a> Elemento Literal  
 Definisce i valori letterali modificabili del frammento di codice. L'elemento `Literal` viene usato per identificare una sostituzione per una parte di codice che è interamente contenuta nel frammento, ma verrà probabilmente personalizzata dopo l'inserimento nel codice. Ad esempio, i valori letterali stringa, i valori numerici e alcuni nomi di variabili dovrebbero essere dichiarati come valori letterali.  
  
 I valori letterali e gli oggetti non possono contenere un elemento **ID** con valore selected o end. Il valore `$selected$` rappresenta il testo selezionato nel documento da inserire nel frammento di codice quando viene richiamato. `$end$` contrassegna il punto in cui posizionare il cursore dopo l'inserimento del frammento di codice.  
  
```xml  
<Literal Editable="true/false">  
   <ID>... </ID>  
   <ToolTip>... </ToolTip>  
   <Default>... </Default>  
   <Function>... </Function>  
</Literal>  
```  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Editable`|Attributo `Boolean` facoltativo. Specifica se il valore letterale può essere modificato o meno dopo l'inserimento del frammento di codice. Il valore predefinito di questo attributo è `true`.|  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Default](../ide/code-snippets-schema-reference.md#default)|Elemento obbligatorio. Specifica il valore predefinito del valore letterale al momento dell'inserimento del frammento di codice. In un elemento `Default` deve essere presente esattamente un elemento `Literal`.|  
|[Elemento Function](../ide/code-snippets-schema-reference.md#function)|Elemento facoltativo. Specifica una funzione da eseguire quando il valore letterale riceve lo stato attivo in Visual Studio. In un elemento `Function` possono essere presenti zero elementi `Literal` oppure uno.|  
|[Elemento ID](../ide/code-snippets-schema-reference.md#id)|Elemento obbligatorio. Specifica un identificatore univoco per il valore letterale. In un elemento `ID` deve essere presente esattamente un elemento `Literal`.|  
|[Elemento ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|Elemento facoltativo. Descrive l'utilizzo e il valore previsti del valore letterale. Possono essere presenti zero o un elemento **Tooltip** in un elemento `Literal`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations)|Contiene i valori letterali e gli oggetti di un frammento di codice che è possibile modificare.|  
  
##  <a name="namespace"></a> Elemento Namespace  
 Specifica lo spazio dei nomi che deve essere importato per la compilazione e l'esecuzione del frammento di codice. Lo spazio dei nomi specificato nell'elemento `Namespace` viene aggiunto automaticamente a un'istruzione `Imports` all'inizio del codice, se non esiste già.  
  
> [!NOTE]
>  L'elemento `Namespace` è supportato solo per i progetti di Visual Basic.  
  
```xml  
<Namespace>  
    Namespace  
</Namespace>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Import](../ide/code-snippets-schema-reference.md#import)|Importa lo spazio dei nomi specificato.|  
  
 È necessario specificare un valore di testo. Questo testo specifica uno spazio dei nomi di cui il frammento di codice presuppone l'importazione.  
  
##  <a name="object"></a> Elemento Object  
 Definisce gli oggetti modificabili del frammento di codice. L'elemento `Object` viene usato per identificare un elemento richiesto dal frammento di codice ma che viene probabilmente definito al di fuori del frammento stesso. È ad esempio opportuno dichiarare come oggetti i controlli Windows Form, i controlli ASP.NET, le istanze di oggetti e le istanze di tipi. Per le dichiarazioni di oggetti è necessario specificare un tipo, usando l'elemento `Type`.  
  
```xml  
<Object Editable="true/false">  
    <ID>... </ID>  
    <Type>... </Type>  
    <ToolTip>... </ToolTip>  
    <Default>... </Default>  
    <Function>... </Function>  
</Object>  
```  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Editable`|Attributo `Boolean` facoltativo. Specifica se il valore letterale può essere modificato o meno dopo l'inserimento del frammento di codice. Il valore predefinito di questo attributo è `true`.|  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Default](../ide/code-snippets-schema-reference.md#default)|Elemento obbligatorio. Specifica il valore predefinito del valore letterale al momento dell'inserimento del frammento di codice. In un elemento `Default` deve essere presente esattamente un elemento `Literal`.|  
|[Elemento Function](../ide/code-snippets-schema-reference.md#function)|Elemento facoltativo. Specifica una funzione da eseguire quando il valore letterale riceve lo stato attivo in Visual Studio. In un elemento `Function` possono essere presenti zero elementi `Literal` oppure uno.|  
|[Elemento ID](../ide/code-snippets-schema-reference.md#id)|Elemento obbligatorio. Specifica un identificatore univoco per il valore letterale. In un elemento `ID` deve essere presente esattamente un elemento `Literal`.|  
|[Elemento ToolTip](../ide/code-snippets-schema-reference.md#tooltip)|Elemento facoltativo. Descrive l'utilizzo e il valore previsti del valore letterale. Possono essere presenti zero o un elemento **Tooltip** in un elemento `Literal`.|  
|[Elemento Type](../ide/code-snippets-schema-reference.md#type)|Elemento obbligatorio. Specifica il tipo di oggetto. In un elemento `Type` deve essere presente esattamente un elemento `Object`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations)|Contiene i valori letterali e gli oggetti di un frammento di codice che è possibile modificare.|  
  
##  <a name="reference"></a> Elemento Reference  
 Specifica informazioni sui riferimenti ad assembly richiesti dal frammento di codice. 
  
```xml  
<Reference>  
    <Assembly>... </Assembly>  
    <Url>... </Url>  
</Reference>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Assembly](../ide/code-snippets-schema-reference.md#assembly)|Elemento obbligatorio. Contiene il nome dell'assembly a cui viene fatto riferimento nel frammento di codice. In un elemento `Assembly` deve essere presente esattamente un elemento `Reference`.|  
|[Elemento Url](../ide/code-snippets-schema-reference.md#url)|Elemento facoltativo. Contiene un URL che fornisce altre informazioni sull'assembly a cui si fa riferimento. In un elemento `Url` possono essere presenti zero elementi `Reference` oppure uno.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento References](../ide/code-snippets-schema-reference.md#references)|Elemento di raggruppamento per elementi `Reference`.|  
  
##  <a name="references"></a> Elemento References  
 Raggruppa singoli elementi `Reference`.  
  
```xml  
<References>  
    <Reference>... </Reference>  
</References>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference)|Elemento facoltativo. Contiene informazioni sui riferimenti ad assembly per il frammento di codice. Possono esistere zero o più elementi `Reference` in un elemento `References`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contiene i riferimenti, le importazioni, le dichiarazioni e il codice del frammento di codice.|  
  
##  <a name="shortcut"></a> Elemento Shortcut  
 Specifica il testo del collegamento usato per inserire il frammento di codice. Il valore di testo di un elemento `Shortcut` può contenere solo caratteri alfanumerici, trattini (-) e caratteri di sottolineatura (_).  
  
> [!CAUTION]
>  I caratteri di sottolineatura (_) e i trattini (-) non sono supportati nei collegamenti dei frammenti di C++.  
  
```xml  
<Shortcut>  
    Shortcut Text  
</Shortcut>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Contiene informazioni generali sul frammento di codice.|  
  
 Il valore di testo è facoltativo. Tale testo viene usato come collegamento per l'inserimento del frammento di codice.  
  
##  <a name="snippet"></a> Elemento Snippet  
 Specifica i riferimenti, le importazioni, le dichiarazione e il codice del frammento di codice.  
  
```xml  
<Snippet>  
    <References>... </References>  
    <Imports>... </Imports>  
    <Declarations>... </Declarations>  
    <Code>... </Code>  
</Snippet>    
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento Code](../ide/code-snippets-schema-reference.md#code)|Elemento obbligatorio. Specifica il codice che si desidera inserire in un file di documentazione. In un elemento `Code` deve essere presente esattamente un elemento `Snippet`.|  
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations)|Elemento facoltativo. Specifica i valori letterali e gli oggetti che costituiscono le parti modificabili di un frammento di codice. In un elemento `Declarations` possono essere presenti zero elementi `Snippet` oppure uno.|  
|[Elemento Imports](../ide/code-snippets-schema-reference.md#imports)|Elemento facoltativo. Raggruppa singoli elementi `Import`. In un elemento `Imports` possono essere presenti zero elementi `Snippet` oppure uno.|  
||Elemento facoltativo. Raggruppa singoli elementi `Reference`. In un elemento `References` possono essere presenti zero elementi `Snippet` oppure uno.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet)|Consente di specificare un'intestazione e più frammenti di codice IntelliSense, che è possibile inserire in file di codice di Visual Studio.|  
  
##  <a name="snippettype"></a> Elemento SnippetType  
 Specifica la modalità di inserimento del frammento di codice.  
  
```xml  
<SnippetType>  
    SurroundsWith/Expansion  
<SnippetType>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes)|Raggruppa gli elementi `SnippetType`.|  
  
 Il valore di testo deve essere uno dei seguenti valori:  
  
-   `SurroundsWith`: consente di inserire il frammento di codice intorno a un segmento di codice selezionato.  
  
-   `Expansion`: consente di inserire il frammento di codice in corrispondenza della posizione del cursore.  
  
-   `Refactoring`: specifica che il frammento di codice viene usato durante il refactoring di C#. Non è possibile usare il `Refactoring` nei frammenti di codice personalizzati.  
  
##  <a name="snippettypes"></a> Elemento SnippetTypes  
 Raggruppa singoli elementi `SnippetType`. Se l'elemento `SnippetTypes` non è presente, il frammento di codice può essere inserito ovunque nel codice.  
  
```xml  
<SnippetTypes>  
    <SnippetType>... </SnippetType>  
    <SnippetType>... </SnippetType>  
<SnippetTypes>  
```  
  
|Elemento figlio|Descrizione|  
|-------------------|-----------------|  
|[Elemento SnippetType](../ide/code-snippets-schema-reference.md#snippettype)|Elemento facoltativo. Specifica la modalità di inserimento del frammento di codice in Visual Studio. Possono esistere zero o più elementi `SnippetType` in un elemento `SnippetTypes`.|  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Specifica informazioni generali sul frammento di codice.|  
  
##  <a name="title"></a> Elemento Title  
 Specifica il titolo del frammento di codice. Il titolo archiviato nell'elemento `Title` del frammento di codice viene visualizzato in **Selezione frammento di codice** e nella descrizione del frammento in **Gestione frammenti di codice**.  
  
```xml  
<Title>  
    Code Snippet Title  
<Title>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Header](../ide/code-snippets-schema-reference.md#header)|Specifica informazioni generali sul frammento di codice.|  
  
 È necessario specificare un valore di testo. Tale testo specifica il titolo del frammento di codice.  
  
##  <a name="tooltip"></a> Elemento ToolTip  
 Descrive la sintassi e il valore previsto di un oggetto o di un valore letterale in un frammento di codice, visualizzati in una descrizione comando durante l'inserimento del frammento di codice in un progetto. Il testo della descrizione comandi viene visualizzato quando il puntatore del mouse viene soffermato sul valore letterale o sull'oggetto dopo l'inserimento del frammento di codice.  
  
```xml  
<ToolTip>  
    ToolTip description  
</ToolTip>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal)|Definisce i campi con valore letterale del frammento di codice che è possibile modificare.|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Definisce i campi di oggetti del frammento di codice che è possibile modificare.|  
  
 È necessario specificare un valore di testo. Tale testo specifica la descrizione della Descrizione comando da associare all'oggetto o al valore letterale nel frammento di codice.  
  
##  <a name="type"></a> Elemento Type  
 Specifica il tipo di oggetto. L'elemento `Object` viene usato per identificare un elemento richiesto dal frammento di codice ma che viene probabilmente definito al di fuori del frammento stesso. È ad esempio opportuno dichiarare come oggetti i controlli Windows Form, i controlli ASP.NET, le istanze di oggetti e le istanze di tipi. Per le dichiarazioni di oggetti è necessario specificare un tipo, usando l'elemento `Type`.  
  
```xml  
<Type>  
    Type  
</Type>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Object](../ide/code-snippets-schema-reference.md#object)|Definisce i campi di oggetti del frammento di codice che è possibile modificare.|  
  
 È necessario specificare un valore di testo. Tale testo specifica il tipo dell'oggetto.  
  
##  <a name="url"></a> Elemento Url  
 Specifica un URL che fornisce altre informazioni sull'assembly a cui viene fatto riferimento.  
  
> [!NOTE]
>  L'elemento `Url` è supportato solo per i progetti di Visual Basic.  
  
```xml  
<Url>  
    www.microsoft.com  
</Url>  
```  
  
|Elemento padre|Descrizione|  
|--------------------|-----------------|  
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference)|Specifica i riferimenti ad assembly richiesti dal frammento di codice.|  
  
 È necessario specificare un valore di testo. Tale testo specifica un URL contenente altre informazioni sull'assembly a cui viene fatto riferimento. L'URL viene visualizzato quando il riferimento non può essere aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice](../ide/code-snippets.md)   
 [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)