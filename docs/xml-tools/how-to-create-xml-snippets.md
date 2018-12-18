---
title: 'Procedura: creare frammenti XML | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 376719363bd97970bdfa333d9aab0e57a8484c73
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-create-xml-snippets"></a>Procedura: creare frammenti XML
L'editor XML può essere usato per creare nuovi frammenti di codice XML. L'editor comprende un frammento di codice XML, denominato "Snippet", ovvero un frammento standard per la creazione di nuovi frammenti di codice XML.  
  
## <a name="to-create-a-new-xml-snippet"></a>Per creare un nuovo frammento di codice XML  
 Per creare un nuovo codice XML frammento di codice, creare un nuovo file XML e utilizzare il **Inserisci frammento di codice** funzionalità.  
  
1.  Nel **File** menu, fare clic su **New** e quindi fare clic su **File**.  
  
2.  Fare clic su **File XML** e quindi fare clic su **aprire**.  
  
3.  Nel riquadro dell'editor e scegliere **Inserisci frammento di codice**.  
  
4.  Selezionare **frammento** dall'elenco e premere INVIO.  
  
5.  Se necessario, apportare modifiche al nuovo frammento.  
  
6.  Dal **File** menu selezionare **Salva XMLFile.xml**.  
  
     Il **Salva File con nome** viene visualizzata la finestra di dialogo.  
  
7.  Immettere il nome per il nuovo frammento di codice e selezionare **file frammento** dal **Salva come** finestra di riepilogo a discesa.  
  
8.  Utilizzare il **salvare in** elenco a discesa per modificare il percorso del file alla cartella Documenti\Visual Studio 2005 Snippets\XML\My XML Snippets e quindi premere **salvare**.  
  
## <a name="snippet-description"></a>Descrizione del frammento di codice  
 Contenuto della sezione vengono descritti alcuni elementi chiave del frammento di codice standard. Per ulteriori informazioni sugli elementi dello schema utilizzato per i frammenti di codice XML, vedere [riferimenti allo Schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).  
  
### <a name="snippettype-element"></a>Elemento SnippetType  
 L'editor supporta due tipi di frammento di codice:  
  
```xml
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```
  
 Il `Expansion` tipo determina se il frammento di codice viene visualizzato quando si richiama il **Inserisci frammento di codice** comando. Il `SurroundsWith` tipo determina se il frammento di codice viene visualizzato quando si richiama il **Racchiudi** comando.  
  
### <a name="code-element"></a>Elemento Code  
 L'elemento `Code` definisce il testo XML che verrà inserito quando viene richiamato il frammento di codice.  
  
> [!NOTE]
>  Il testo del frammento di codice XML deve essere racchiuso in una sezione `<![CDATA[...]]>`.  
  
 Di seguito viene riportato l'elemento `Code` creato dal frammento standard.  
  
```xml
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```
  
 L'elemento `Code` comprende tre variabili.  
  
-   $name$ è la variabile definita dall'utente e consente di creare un elemento `name`, che presenta un valore modificabile il cui valore predefinito è "name". Le variabili definite dall'utente vengono definite usando l'elemento `Literal`.  
  
-   $selected$ è una variabile predefinita e rappresenta il testo che era stato selezionato nell'editor XML prima di richiamare il frammento di codice. La posizione di questa variabile determina la posizione del testo selezionato nel frammento di codice che racchiude la selezione.  
  
-   $end$ è una variabile predefinita. Quando l'utente preme INVIO per terminare la modifica dei campi del frammento di codice, la variabile determina la posizione in cui viene spostato l'accento circonflesso (^).  
  
 L'elemento `Code` consente l'inserimento del testo XML seguente:  
  
```xml
<test>  
  <name>name</name>  
</test>  
```
  
 Il valore dell'elemento nome viene contrassegnato come area modificabile.  
  
### <a name="literal-element"></a>Elemento Literal  
 L'elemento `Literal` viene usato per identificare il testo di sostituzione che è possibile personalizzare dopo che è stato inserito nel file. Ad esempio, le stringhe letterali, i valori numerici e alcuni nomi di variabili possono essere dichiarati come letterali. È possibile definire un qualsiasi numero di valori formali nel frammento di codice XML e farvi riferimento più volte dall'interno del frammento. Di seguito viene riportato un esempio di elemento `Literal` che definisce una variabile $name$ il cui valore predefinito è "name."  
  
```xml
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```
  
 I valori formali possono anche fare riferimento a funzioni. L'Editor XML include una funzione denominata **LookupPrefix**. Il **LookupPrefix** funzione Cerca l'URI dello spazio dei nomi specificato dalla posizione nel documento XML che questo frammento viene richiamato da e restituisce il prefisso dello spazio dei nomi definito per tale spazio dei nomi, se presente, e include i due punti (:) in tale nome. Di seguito è riportato un esempio di un `Literal` elemento che utilizza il **LookupPrefix** (funzione).  
  
```xml
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```
  
 La variabile $prefix$ può quindi essere usata in altri punti all'interno del frammento di codice XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice XML](../xml-tools/xml-snippets.md)   
 [Procedura: utilizzare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Procedura: Generare un frammento XML da XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)