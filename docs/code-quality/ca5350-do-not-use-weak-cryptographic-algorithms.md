---
title: 'CA5350: Non utilizzare algoritmi di crittografia vulnerabili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6672922343ef6c0b56dd91eb358cf2fcd7ac6090
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: non usare algoritmi di crittografia vulnerabili
|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Category|Microsoft.Cryptography|  
|Modifica importante|Non importante|  
  
> [!NOTE]
>  Ultimo aggiornamento di questo avviso: novembre 2015.  
  
## <a name="cause"></a>Causa  
 Gli algoritmi di crittografia, ad esempio <xref:System.Security.Cryptography.TripleDES> e gli algoritmi di hash, ad esempio <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> sono considerati vulnerabili.  
  
 Questi algoritmi di crittografia non assicurano la sicurezza tanto quanto le controparti più moderne. Gli algoritmi di hash crittografici <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> forniscono meno resistenza ai conflitti rispetto agli algoritmi di hash più moderni. L'algoritmo di crittografia <xref:System.Security.Cryptography.TripleDES> fornisce un minor numero di bit di sicurezza rispetto ad algoritmi di crittografia più moderni.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza dei dati che proteggono.  
  
 La regola viene attivata quando trova algoritmi 3DES, SHA1 o RIPEMD160 nel codice e genera un avviso all'utente.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Usare opzioni di crittografia più avanzate:  
  
-   Per la crittografia TripleDES, usare la crittografia <xref:System.Security.Cryptography.Aes> .  
  
-   Per le funzioni hash SHA1 o RIPEMD160, usare quelle nella [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) famiglia (ad esempio <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola quando il livello di protezione necessario per i dati non richiede una garanzia di sicurezza.  
  
## <a name="pseudo-code-example"></a>Esempio di pseudocodice  
 Al momento della stesura di questo articolo, l'esempio di pseudocodice seguente illustra il modello rilevato da questa regola.  
  
### <a name="sha-1-hashing-violation"></a>Violazione di hash SHA-1  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA1.Create();  
  
```  
  
### <a name="solution"></a>Soluzione  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Violazione di hash  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### <a name="solution"></a>Soluzione  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="tripledes-encryption-violation"></a>Violazione di crittografia TripleDES  
  
```  
using System.Security.Cryptography;   
...    
using (TripleDES encAlg = TripleDES.Create())   
{   
  ...   
}  
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