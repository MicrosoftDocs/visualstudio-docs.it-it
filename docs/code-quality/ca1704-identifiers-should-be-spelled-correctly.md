---
title: 'CA1704: Gli identificatori devono essere digitati correttamente'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6fe8c51ce1fc2bd93fca26b52b3ef5daf223b8b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Gli identificatori devono essere digitati correttamente

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft. Questa regola non controlla costruttori o membri denominato speciali, ad esempio get e set di funzioni di accesso alle proprietà.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza l'identificatore per i token e controlla l'ortografia di ogni token. Algoritmo di analisi vengono eseguite le trasformazioni seguenti:

- Lettere maiuscole avviare un nuovo token. Ad esempio, MyNameIsJoe deamon "My", "Name", "Is", "Joe".

- Per le lettere maiuscole più, l'ultima lettera maiuscola inizia un nuovo token. Ad esempio, GUIEditor viene scomposto nei token "GUI", "Editor".

- Iniziali e finali apostrofi vengono rimossi. Ad esempio, 'sender' deamon "mittente".

- Caratteri di sottolineatura indicano la fine di un token e vengono rimossi. Ad esempio, Hello_world deamon di "Hello", "world".

- Le e commerciali incorporate vengono rimossi. Ad esempio, for&mat viene scomposto nel token "format".

## <a name="language"></a>Linguaggio

Il correttore ortografico attualmente controlla solo a dizionari le impostazioni cultura basate su inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto, aggiungendo il **CodeAnalysisCulture** elemento.

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore diverso da delle impostazioni cultura basate su inglese, questa regola di analisi codice invisibile all'utente è disabilitata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola al dizionario personalizzato.

### <a name="to-add-words-to-a-custom-dictionary"></a>Per aggiungere parole a un dizionario personalizzato

Denominare il file XML del dizionario personalizzato *DizionarioPersonale*. Inserire il dizionario nella directory di installazione dello strumento, nella directory del progetto o nella directory associata con lo strumento sotto il profilo dell'utente (*%USERPROFILE%\Application dati\\...* ). Per informazioni su come aggiungere il dizionario personalizzato a un progetto in Visual Studio, vedere [procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Aggiungere le parole che non dovrebbero causare una violazione in un percorso Dictionary/Words/Recognized.

- Aggiungere le parole che devono causare una violazione in un percorso dizionario/parole/non riconosciuto.

- Aggiungere le parole che devono essere contrassegnate come obsoleto nel percorso Dictionary/Words/Deprecated. Vedere l'argomento di regola correlata [CA1726: utilizzare termini Preferiti](../code-quality/ca1726-use-preferred-terms.md) per ulteriori informazioni.

- Aggiungere le eccezioni alle regole per il percorso di dizionario/acronimi/CasingExceptions maiuscole e minuscole degli acronimi.

Di seguito è riportato un esempio della struttura di un file del dizionario personalizzato:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Escludere un avviso da questa regola solo se la parola è intenzionalmente errata e di word viene applicata a un set limitato della libreria. Correttamente ortografia consente di ridurre la curva di apprendimento che è necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
