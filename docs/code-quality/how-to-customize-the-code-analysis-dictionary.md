---
title: 'Procedura: Personalizzare il dizionario di analisi del codice'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 544343a701909957ff0c16a49beeaf081cf256b8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procedura: Personalizzare il dizionario di analisi del codice
Analisi del codice utilizza un dizionario incorporato per controllare gli identificatori nel codice per errori di ortografia, maiuscole e altre convenzioni di denominazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] linee guida. È possibile creare un file Xml del dizionario personalizzato per aggiungere, rimuovere o modificare i termini e abbreviazioni acronimi nel dizionario incorporato.

 Ad esempio, si supponga che il codice contiene una classe denominata **contraccolpo**. Analisi del codice identifica il nome come un insieme di due parole: **sportello** e **colpo**. Verrà generato un avviso che **colpo** non sia stato digitato correttamente. Per forzare l'analisi del codice per riconoscere l'ortografia, è possibile aggiungere il termine **colpo** al dizionario personalizzato.

## <a name="to-create-a-custom-dictionary"></a>Per creare un dizionario personalizzato
 Creare un file denominato **DizionarioPersonale**.

 Definire le parole personalizzate utilizzando la struttura XML seguente:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Elementi del dizionario personalizzato
 È possibile modificare il comportamento del dizionario di analisi del codice tramite l'aggiunta di condizioni come testo interno degli elementi seguenti nel dizionario personalizzato:

-   [Dizionario/parole/riconosciuto/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

-   [Dizionario/parole/non riconosciuto/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

-   [Dizionario/parole/deprecato/Term [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

-   [Dizionario/parole/Compound/Term [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

-   [Dizionario/parole/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

-   [Dizionario/acronimi/CasingExceptions/acronimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dizionario/parole/riconosciuto/Word
 Per includere un termine nell'elenco dei termini che l'analisi del codice identifica come digitati correttamente, aggiungere il termine come testo interno di un elemento Dictionary/Words/Recognized/Word. Condizioni negli elementi Dictionary/Words/Recognized/Word non sono rilevanti.

 **Esempio**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Condizioni in nodi Dictionary/Words/Recognized vengono applicate le regole di analisi di codice seguente:

-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dizionario/parole/non riconosciuto/Word
 Per escludere un termine dall'elenco dei termini che l'analisi del codice identifica come digitati correttamente, aggiungere il termine come testo interno di un elemento del dizionario/parole, non riconosciuto o Word. Condizioni negli elementi Dictionary/parole, non riconosciuto/Word non sono rilevanti.

 **Esempio**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Nel nodo Dictionary/Words/Unrecognized termini vengono applicati le regole di analisi di codice seguente:

-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dizionario/parole/deprecato/Term [@PreferredAlternate]
 Per includere un termine nell'elenco dei termini che l'analisi del codice identifica come deprecati, aggiungere il termine come testo interno di un elemento/parole dizionario/Term obsoleto. Un termine deprecato è una parola che sia stata digitata correttamente, ma non deve essere utilizzata.

 Per includere un termine alternativo suggerito nel messaggio di avviso, specificare l'alternativa nell'attributo PreferredAlternate dell'elemento Term. Se non si desidera suggerire un'alternativa, è possibile lasciare vuoto il valore dell'attributo.

-   Il termine obsoleto nel dizionario o parole/elemento deprecato/termine non è tra maiuscole e minuscole.

-   Il valore dell'attributo PreferredAlternate è tra maiuscole e minuscole. La convenzione Pascal caso di utilizzo per le alternative composte.

 **Esempio**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>

```

 Nel nodo Dictionary/Words/Deprecated termini vengono applicati le regole di analisi di codice seguente:

-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dizionario/parole/Compound/Term [@CompoundAlternate]
 Il dizionario incorporato identifica alcuni termini come singoli termini discreti, anziché un termine composto. Per includere un termine nell'elenco dei termini che l'analisi del codice identifica come una parola composta e specificare le maiuscole e minuscole corrette del termine, aggiungere il termine come testo interno di un elemento Dictionary/Words/Compound/Term. Nell'attributo dell'elemento Term CompoundAlternate, specificare le singole parole che compongono il termine composto da una conversione in maiuscolo la prima lettera delle singole parole (convenzione Pascal). Si noti che il termine specificato nel testo interno viene automaticamente aggiunto all'elenco di parole/dizionario/DiscreteExceptions.

-   Il termine obsoleto nel dizionario o parole/elemento deprecato/termine non è tra maiuscole e minuscole.

-   Il valore dell'attributo PreferredAlternate è tra maiuscole e minuscole. La convenzione Pascal caso di utilizzo per le alternative composte.

 **Esempio**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>

```

 Termini nel nodo parole/dizionario/composta vengono applicati le regole di analisi di codice seguente:

-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dizionario/parole/DiscreteExceptions/Term
 Per escludere un termine nell'elenco dei termini che l'analisi del codice identifica come singolo, word discreti quando il termine viene controllato dalle regole di maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento del dizionario/Words/DiscreteExceptions/Term. Il termine nell'elemento Dictionary/Words/DiscreteExceptions/Term non è tra maiuscole e minuscole.

 **Esempio**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>

```

 Nel nodo Dictionary/Words/DiscreteExceptions termini vengono applicati le regole di analisi di codice seguente:

-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dizionario/acronimi/CasingExceptions/acronimo
 Per includere un acronimo nell'elenco dei termini che l'analisi del codice identifica come sia stata digitata correttamente e indicare come l'acronimo quando il termine è selezionato per le maiuscole e minuscole delle regole per le parole composte, aggiungere il termine come testo interno di un dizionario, gli acronimi/CasingExceptions / Elemento di un acronimo. L'acronimo nell'elemento Dictionary/acronimi/CasingExceptions/Acronym è tra maiuscole e minuscole.

 **Esempio**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>

```

 Nel nodo acronimi/dizionario/CasingExceptions termini vengono applicati le regole di analisi di codice seguente:

-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Per applicare un dizionario personalizzato a un progetto

1.  In **Esplora**, utilizzare una delle procedure riportate di seguito:

2.  Per aggiungere un dizionario per un singolo progetto, fare doppio clic il nome del progetto e quindi fare clic su **Aggiungi elemento esistente**. Specificare il file di **Aggiungi elemento esistente** la finestra di dialogo.

3.  Per aggiungere un dizionario che viene condiviso tra due o più progetti, individuare il file da condividere il **Aggiungi elemento esistente** finestra di dialogo casella, fare clic sulla freccia rivolta verso il basso il **Aggiungi** pulsante e quindi fare clic su **Aggiungi come collegamento** .

4.  In **Esplora**, fare doppio clic su di **DizionarioPersonale** nome file e fare clic su **proprietà**.

5.  Dal **azione di compilazione** elenco, selezionare **CodeAnalysisDictionary**.

6.  Dal **copia nella Directory di Output di** elenco, selezionare **non copiare**.