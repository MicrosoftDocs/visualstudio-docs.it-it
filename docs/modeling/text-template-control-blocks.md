---
title: Blocchi di controllo del modello di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 221985f8bfbac82e294422c57d684322b9036d5f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="text-template-control-blocks"></a>Blocchi di controllo del modello di testo
I blocchi di controllo consentono di scrivere codice nel modello di testo per variare l'output. Esistono tre tipi di blocchi di controllo, distinguibili dalla parentesi di apertura:

-   `<# Standard control blocks #>` può contenere istruzioni.

-   `<#= Expression control blocks #>` può contenere espressioni.

-   `<#+ Class feature control blocks #>` può contenere metodi, campi e proprietà.

## <a name="standard-control-block"></a>Blocco di controllo standard
 I blocchi di controllo standard contengono istruzioni. Ad esempio, il blocco standard seguente ottiene i nomi di tutti gli attributi nel documento XML:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 È possibile incorporare testo normale all'interno di un'istruzione composta quale `if` o `for`. Questo frammento, ad esempio, genera una riga di output in ogni iterazione del ciclo:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
>  Usare sempre {...} per delimitare istruzioni annidate contenenti testo normale incorporato. L'esempio seguente non funziona correttamente:
>
>  `<# if (ShouldPrint) #> Some text. -- WRONG`
>
>  È invece necessario usare parentesi graffe {}, come indicato di seguito:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>

```

## <a name="expression-control-block"></a>Blocco di controllo dell'espressione
 I blocchi di controllo dell'espressione vengono usati per il codice che fornisce stringhe da scrivere nel file di output. Ad esempio, l'esempio precedente consente di stampare i nomi degli attributi nel file di output modificando il blocco di codice come segue:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Blocco di controllo della funzionalità di classe
 È possibile usare i blocchi di controllo della funzionalità di classe per aggiungere al modello di testo metodi, proprietà, campi o persino classi annidate. L'uso più comune dei blocchi della funzionalità di classe è fornire funzioni di supporto per il codice in altre parti del modello di testo. Ad esempio, il blocco della funzionalità di classe seguente converte in maiuscolo la prima lettera del nome dell'attributo, oppure, se il nome contiene spazi vuoti, converte in maiuscolo la prima lettera di ogni parola:

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
>  Un blocco di controllo della funzionalità di classe non deve essere seguito da blocchi di controllo standard nello stesso file modello. Questa restrizione, tuttavia, non si applica al risultato dell'uso di direttive `<#@include#>`. Ogni file incluso può contenere blocchi standard seguiti da blocchi della funzionalità di classe.

 È possibile creare una funzione che genera output incorporando testo e blocchi espressione all'interno di un blocco di controllo delle funzionalità di classe. Ad esempio:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 È possibile chiamare questa funzione da un blocco standard o da un altro blocco delle funzionalità di classe:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Come usare i blocchi di controllo
 Tutto il codice in tutti i blocchi di controllo standard ed espressione in un unico modello (compreso tutto il codice nei modelli inclusi) viene combinato per formare il metodo `TransformText()` del codice generato. (Per ulteriori informazioni su come includere altri modelli di testo con il `include` direttiva, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).)

 Quando si usano i blocchi di controllo, è necessario tenere presenti le considerazioni seguenti:

-   **Lingua.** In un modello di testo è possibile usare codice C# o Visual Basic. Il linguaggio predefinito è C#, ma è possibile specificare Visual Basic nel parametro `language` della direttiva `template`. (Per ulteriori informazioni sul `template` direttiva, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).)

     Il linguaggio usato nei blocchi di controllo non ha nulla a che fare con il linguaggio o il formato del testo generato in un modello di testo. È possibile generare codice C# usando codice Visual Basic o viceversa.

     È possibile usare un solo linguaggio in un modello di testo specifico, compresi tutti i modelli di testo presenti nella direttiva `include`.

-   **Variabili locali.** Tutto il codice dei blocchi di controllo standard e dell'espressione in un modello di testo viene generato come metodo singolo. È pertanto necessario assicurarsi che non sorgano conflitti con i nomi delle variabili locali. Se si desidera includere altri modelli di testo, è necessario assicurarsi che i nomi delle variabili siano univoci per tutti i modelli inclusi. Un modo per garantire questo risultato consiste nell'aggiungere a ogni nome di variabile locale una stringa che identifichi il modello di testo in cui la variabile è stata dichiarata.

     È inoltre consigliabile inizializzare le variabili locali su valori ragionevoli al momento della dichiarazione, in particolare quando si includono più modelli di testo.

-   **Annidamento di blocchi di controllo.** I blocchi di controllo non possono essere annidati l'uno nell'altro. Prima di aprirne un altro, è sempre necessario terminare un blocco di controllo specifico. Ad esempio, di seguito viene illustrato come stampare testo in un blocco espressione come parte di un blocco di controllo standard.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

-   **Il refactoring.** Per garantire la brevità e la comprensibilità dei modelli di testo, è consigliabile evitare di usare codice ripetitivo eseguendo il factoring del codice riutilizzabile all'interno di funzioni di supporto nei blocchi della funzionalità di classe o creando una classe di modello di testo personale che eredita dalla classe Microsoft.VisualStudio.TextTemplating.TextTransformation.