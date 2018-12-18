---
title: 'CA5351: non usare algoritmi di crittografia interrotti'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0269a5373249e93903e9cf82ceaa0a6a674b3def
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: non usare algoritmi di crittografia interrotti
|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Category|Microsoft.Cryptography|
|Modifica importante|Non importante|

> [!NOTE]
>  Ultimo aggiornamento di questo avviso: novembre 2015.

## <a name="cause"></a>Causa
 Le funzioni hash come <xref:System.Security.Cryptography.MD5> e gli algoritmi di crittografia come <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> possono causare rischi significativi ed esporre le informazioni sensibili tramite semplici tecniche di attacco, come attacchi di forza bruta e collisioni hash.

 Gli algoritmi di crittografia elencati di seguito sono soggetti ad attacchi crittografici noti. L'algoritmo hash di crittografia <xref:System.Security.Cryptography.MD5> è soggetto ad attacchi di collisione hash.  A seconda dell'utilizzo, la collisione hash può causare rappresentazione, manomissione o altri tipi di attacchi in sistemi che ricorrono all'output di crittografia univoco di una funzione hash. Gli algoritmi di crittografia <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> sono soggetti ad attacchi crittografici che possono provocare la diffusione indesiderata dei dati crittografati.

## <a name="rule-description"></a>Descrizione della regola
 Gli algoritmi di crittografia interrotti non sono considerati sicuri e il loro uso non è consigliato. L'algoritmo hash MD5 è soggetto ad attacchi di collisione noti, anche se la vulnerabilità specifica varia a seconda del contesto d'uso.  Gli algoritmi hash usati per garantire l'integrità dei dati (ad esempio una firma del file o un certificato digitale) sono particolarmente vulnerabili.  In questo contesto gli autori di attacchi possono generare due serie di dati separati, in modo tale che i dati validi possano essere sostituiti da dati dannosi senza modificare il valore hash o invalidare una firma digitale associata.

 Per gli algoritmi di crittografia:

-   La crittografia<xref:System.Security.Cryptography.DES> contiene una chiave di piccole dimensioni, che può essere colpita da attacchi di forza bruta in meno di un giorno.

-   La crittografia<xref:System.Security.Cryptography.RC2> è soggetta ad attacchi alle chiavi correlate, in cui l'autore dell'attacco trova le relazioni matematiche tra tutti i valori di chiave.

 Questa regola viene attivata quando trova nel codice sorgente una delle funzioni di crittografia indicate sopra e genera un avviso all'utente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Usare opzioni di crittografia più avanzate:

-   Per MD5, usare l'hash nel [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) famiglia (ad esempio <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

-   Per DES e RC2, usare la crittografia <xref:System.Security.Cryptography.Aes> .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola, a meno che questa non venga esaminata da un esperto di crittografia.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice
 L'esempio di pseudocodice seguente mostra il criterio rilevato da questa regola e le possibili alternative.

### <a name="md5-hashing-violation"></a>Violazione di hash MD5

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Soluzione

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>Violazione di crittografia RC2

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

```

### <a name="solution"></a>Soluzione

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Violazione di crittografia

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

```

### <a name="solution"></a>Soluzione

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```