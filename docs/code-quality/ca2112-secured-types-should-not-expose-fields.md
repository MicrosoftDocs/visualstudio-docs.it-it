---
title: 'CA2112: I tipi protetti non devono esporre campi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3959540d00a74d99095a3facf824d822827a00d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: I tipi protetti non devono esporre campi
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto contiene campi pubblici ed è protetto da un [le richieste di collegamento](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare i campi non pubblici e aggiungere metodi che restituiscono i dati del campo o proprietà pubbliche. Controlli di sicurezza LinkDemand sui tipi di proteggere l'accesso a proprietà e metodi del tipo. Sicurezza dall'accesso di codice, tuttavia, non si applica ai campi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Per problemi di sicurezza sia per una progettazione ottimale, è necessario correggere le violazioni rendendo non pubblici campi pubblici. È possibile escludere un avviso da questa regola se il campo non contiene informazioni che devono rimanere protette e non fare affidamento sul contenuto del campo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è costituito da una libreria di tipi (`SecuredTypeWithFields`) con campi non protetti, un tipo (`Distributor`) che consente di creare istanze del tipo di libreria e istanze passate erroneamente a tipi non dispone delle autorizzazioni necessarie per crearli e il codice dell'applicazione può leggere i campi di un'istanza anche se non dispone dell'autorizzazione che protegge il tipo.  
  
 Il seguente codice di libreria viola la regola.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>Esempio  
 L'applicazione non è possibile creare un'istanza a causa la richiesta di collegamento che protegge il tipo protetto. La classe seguente consente all'applicazione ottenere un'istanza del tipo protetto.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>Esempio  
 Applicazione riportata di seguito viene illustrato come, senza l'autorizzazione per accedere ai metodi di un tipo protetta, accessibile dal codice i relativi campi.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 Questo esempio produce il seguente output:  
  
 **Creazione di un'istanza di SecuredTypeWithFields.**  
**Campi di tipo protetti: 22, 33**  
**Modifica il campo tipo protetto...**  
**Memorizzato nella cache di campi dell'oggetto: 99, 33**   
## <a name="related-rules"></a>Regole correlate  
 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)   
 [Dati e modellazione](/dotnet/framework/data/index)