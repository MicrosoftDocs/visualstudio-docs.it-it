---
title: 'CA1704: Gli identificatori devono essere digitati correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63b10dd1d1037ee90156505f2e73105be7a9ee63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Gli identificatori devono essere digitati correttamente
|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Category|Microsoft. naming|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft. Questa regola non controlla costruttori o membri denominato speciali, ad esempio get e set di funzioni di accesso alle proprietà.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola analizza l'identificatore per i token e controlla l'ortografia di ogni token. Algoritmo di analisi vengono eseguite le trasformazioni seguenti:  
  
-   Lettere maiuscole avviare un nuovo token. Ad esempio, MyNameIsJoe deamon "My", "Name", "Is", "Joe".  
  
-   Per le lettere maiuscole più, l'ultima lettera maiuscola inizia un nuovo token. Ad esempio, GUIEditor viene scomposto nei token "GUI", "Editor".  
  
-   Iniziali e finali apostrofi vengono rimossi. Ad esempio, 'sender' deamon "mittente".  
  
-   Caratteri di sottolineatura indicano la fine di un token e vengono rimossi. Ad esempio, Hello_world deamon di "Hello", "world".  
  
-   Le e commerciali incorporate vengono rimossi. Ad esempio, for&mat viene scomposto nel token "format".  
  
 Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Nessun altri dizionari sono attualmente disponibili.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola al dizionario personalizzato denominato CustomDictionary. Inserire il dizionario nella directory di installazione dello strumento, nella directory del progetto o nella directory associata allo strumento nel profilo dell'utente (%USERPROFILE%\Application dati\\...). Per informazioni su come aggiungere il dizionario personalizzato a un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [procedura: personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Aggiungere le parole che non dovrebbero causare una violazione in un percorso Dictionary/Words/Recognized.  
  
-   Aggiungere le parole che devono causare una violazione in un percorso dizionario/parole/non riconosciuto.  
  
-   Aggiungere le parole che devono essere contrassegnate come obsoleto nel percorso Dictionary/Words/Deprecated. Vedere l'argomento di regola correlata [CA1726: utilizzare termini Preferiti](../code-quality/ca1726-use-preferred-terms.md) per ulteriori informazioni.  
  
-   Aggiungere le eccezioni alle regole per il percorso di dizionario/acronimi/CasingExceptions maiuscole e minuscole degli acronimi.  
  
 Di seguito è riportato un esempio della struttura di un file del dizionario personalizzato.  
  
```  
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
 [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
