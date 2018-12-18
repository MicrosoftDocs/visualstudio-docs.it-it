---
title: 'CA2201: Non generare tipi di eccezione riservati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11e00594c1cf279fb6b07791bb48f2222cc9c79b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Non generare tipi di eccezione riservati
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Category|Microsoft. Usage|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo genera un tipo di eccezione troppo generale o che è riservato dal runtime.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I seguenti tipi di eccezione sono troppo generici per fornire informazioni sufficienti per l'utente:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 I seguenti tipi di eccezione sono riservati e devono essere generati solo da common language runtime:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Non generare eccezioni generali**  
  
 Se si genera un tipo di eccezione generale, ad esempio <xref:System.Exception> o <xref:System.SystemException> in una libreria o framework, saranno costretti a rilevare tutte le eccezioni, incluse le eccezioni sconosciute che non sono progettati gestire.  
  
 Al contrario, generare un tipo più derivato esiste già nel framework oppure creare un nuovo tipo che deriva da <xref:System.Exception>.  
  
 **Generare eccezioni specifiche**  
  
 Nella tabella seguente vengono illustrati i parametri e le eccezioni da generare quando si convalida il parametro, incluso il parametro di valore nella funzione di accesso set di una proprietà:  
  
|Descrizione parametro|Eccezione|  
|---------------------------|---------------|  
|`null`riferimento|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Compreso nell'intervallo consentito di valori (ad esempio un indice per un elenco o raccolta)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Non valido `enum` valore|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contiene un formato che non soddisfa le specifiche del parametro di un metodo (ad esempio la stringa di formato per `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|Non è valida|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Quando un'operazione non è valida per lo stato corrente di un oggetto generare<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Generata quando viene eseguita un'operazione su un oggetto che è stato eliminato<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Quando un'operazione non supportata (ad esempio un sottoposto a override **oggetto Stream. Write** in un flusso aperto per la lettura) throw<xref:System.NotSupportedException?displayProperty=fullName>  
  
 Generata quando una conversione comporterebbe un overflow (ad esempio un overload dell'operatore di cast esplicito)<xref:System.OverflowException?displayProperty=fullName>  
  
 Per tutti gli altri casi, è consigliabile creare un proprio tipo che deriva da <xref:System.Exception> e generarlo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo dell'eccezione generata in un tipo specifico che non è uno dei tipi riservati.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)