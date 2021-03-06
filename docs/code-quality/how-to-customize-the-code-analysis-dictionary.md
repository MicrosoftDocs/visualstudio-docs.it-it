---
title: 'Procedura: Personalizzare il dizionario di analisi del codice'
ms.date: 11/04/2016
description: Informazioni sul dizionario di analisi del codice che identifica gli errori di ortografia e convenzione di denominazione. Vedere come creare un dizionario personalizzato e applicarlo a un progetto.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10466acedcd5c7f5fda835d66e654128a556d0a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860100"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procedura: Personalizzare il dizionario di analisi del codice

L'analisi del codice usa un dizionario incorporato per controllare gli identificatori nel codice per gli errori di ortografia, maiuscole e minuscole e altre convenzioni di denominazione delle linee guida di progettazione .NET. È possibile creare un file XML dizionario personalizzato per aggiungere, rimuovere o modificare termini, abbreviazioni e acronimi nel dizionario predefinito.

Si supponga, ad esempio, che il codice contenesse una classe denominata **contraccolpo**. L'analisi del codice identifica il nome come composto da due parole: **door** e **knokker**. Genera quindi un avviso che indica che il valore di **knokker** non è stato digitato correttamente. Per forzare l'analisi del codice in modo che riconosca l'ortografia, è possibile aggiungere il termine **knokker** al dizionario personalizzato.

## <a name="to-create-a-custom-dictionary"></a>Per creare un dizionario personalizzato

Creare un file denominato **CustomDictionary.xml**.

Definire le parole personalizzate utilizzando la struttura XML seguente:

```xml
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

## <a name="custom-dictionary-elements"></a>Elementi dizionario personalizzati

È possibile modificare il comportamento del dizionario di analisi del codice aggiungendo termini come testo interno dei seguenti elementi nel dizionario personalizzato:

- [Dizionario/parole/riconosciute/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dizionario/parole/non riconosciuto/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/deprecato/termine [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/Words/Compound/Term [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dizionario/parole/DiscreteExceptions/termine](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dizionario/acronimi/CasingExceptions/acronimo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Dizionario/parole/riconosciute/Word

Per includere un termine nell'elenco dei termini identificati correttamente dall'analisi codice, aggiungere il termine come testo interno di un elemento Dictionary/Words/Recognized/Word. I termini negli elementi Dictionary/Words/Recognized/Word non fanno distinzione tra maiuscole e minuscole.

**Esempio**

```xml
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

I termini in dizionario/parole/nodi riconosciuti vengono applicati alle seguenti regole di analisi del codice:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dizionario/parole/non riconosciuto/Word

Per escludere un termine dall'elenco dei termini identificati correttamente dall'analisi codice, aggiungere il termine da escludere come testo interno di un elemento Dictionary/Words/Unrecognized/Word. I termini negli elementi Dictionary/Words/Unrecognized/Word non fanno distinzione tra maiuscole e minuscole.

**Esempio**

```xml
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

I termini del nodo dizionario/parole/non riconosciuto vengono applicati alle seguenti regole di analisi del codice:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary/Words/deprecato/termine [ @PreferredAlternate ]

Per includere un termine nell'elenco di termini che l'analisi del codice identifica come deprecata, aggiungere il termine come testo interno di un elemento Dictionary/Words/Deprecated/Term. Un termine deprecato è una parola che è stata digitata correttamente, ma non deve essere utilizzata.

Per includere un termine alternativo suggerito nell'avviso, specificare l'alternativa nell'attributo PreferredAlternate dell'elemento term. Se non si desidera suggerire un'alternativa, è possibile lasciare vuoto il valore dell'attributo.

- Il termine deprecato nell'elemento Dictionary/Words/Deprecated/Term non fa distinzione tra maiuscole e minuscole.

- Il valore dell'attributo PreferredAlternate fa distinzione tra maiuscole e minuscole. Usare il caso Pascal per le alternative composte.

**Esempio**

```xml
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

Le condizioni nel nodo dizionario/parole/deprecato vengono applicate alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

- [CA1726: Usare termini preferiti](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/Words/Compound/Term [ @CompoundAlternate ]

Il dizionario incorporato identifica alcuni termini come singoli termini discreti anziché come un termine composto. Per includere un termine nell'elenco di termini che l'analisi codice identifica come una parola composta e per specificare la combinazione di maiuscole e minuscole corretta del termine, aggiungere il termine come testo interno di un elemento Dictionary/Words/Compound/Term. Nell'attributo CompoundAlternate dell'elemento term specificare le singole parole che compongono il termine composto capitalizzando la prima lettera delle singole parole (caso Pascal). Si noti che il termine specificato nel testo interno viene aggiunto automaticamente all'elenco dizionario/parole/DiscreteExceptions.

- Il termine composto nell'elemento Dictionary/Words/Compound/Term non distingue tra maiuscole e minuscole.

- Il valore dell'attributo CompoundAlternate fa distinzione tra maiuscole e minuscole. Usare il caso Pascal per le alternative composte.

**Esempio**

```xml
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

I termini nel nodo Dictionary/Words/Compound vengono applicati alle seguenti regole di analisi del codice:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703.md)

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dizionario/parole/DiscreteExceptions/termine

Per escludere un termine nell'elenco di termini che l'analisi del codice identifica come una singola parola discreta quando il termine viene controllato dalle regole di combinazione di maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento Dictionary/Words/DiscreteExceptions/Term. Il termine nell'elemento Dictionary/Words/DiscreteExceptions/Term non fa distinzione tra maiuscole e minuscole.

**Esempio**

```xml
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

Le condizioni nel nodo Dictionary/Words/DiscreteExceptions vengono applicate alle regole di analisi del codice seguenti:

- [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701.md)

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dizionario/acronimi/CasingExceptions/acronimo

Per includere un acronimo nell'elenco di termini che l'analisi del codice identifica come digitato correttamente e per indicare in che modo l'acronimo viene controllato dalle regole per la combinazione di maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento Dictionary/Acronims/CasingExceptions/acronimo. Per l'acronimo nell'elemento Dictionary/Acronims/CasingExceptions/acronimo viene fatta distinzione tra maiuscole e minuscole.

**Esempio**

```xml
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

Le condizioni nel nodo Dictionary/Acronims/CasingExceptions vengono applicate alle seguenti regole di analisi del codice:

- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Per applicare un dizionario personalizzato a un progetto

1. In **Esplora soluzioni** usare una delle procedure seguenti:

    - Per aggiungere un dizionario a un singolo progetto, fare clic con il pulsante destro del mouse sul nome del progetto, quindi scegliere **Aggiungi elemento esistente**. Specificare il file nella finestra di dialogo **Aggiungi elemento esistente** .
  
    - Per aggiungere un dizionario condiviso tra due o più progetti, individuare il file da condividere nella finestra di dialogo **Aggiungi elemento esistente** , fare clic sulla freccia in giù del pulsante **Aggiungi** e quindi fare clic su **Aggiungi come collegamento**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del file **CustomDictionary.xml** e scegliere **proprietà**.

3. Dall'elenco **azione di compilazione** selezionare **CodeAnalysisDictionary**.

4. Dall'elenco **copia in directory di output** selezionare **non copiare**.
