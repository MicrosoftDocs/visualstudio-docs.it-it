---
title: 'CA1822: Contrassegna i membri come statici | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1f3c20f39fe863925d46c1f86f2f6a821e8489a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Contrassegna i membri come statici
|||  
|-|-|  
|TypeName|MarkMethodsAsStatic|  
|CheckId|CA1822|  
|Category|Microsoft. Performance|  
|Modifica importante|Non sostanziale - Se il membro non è visibile all'esterno dell'assembly, indipendentemente dal fatto le modifiche apportate. Non sostanziale - Se si modifica solo il membro a un membro di istanza con il `this` (parola chiave).<br /><br /> Sostanziale - Se si modifica il membro da un membro di istanza a un membro statico e è visibile all'esterno dell'assembly.|  
  
## <a name="cause"></a>Causa  
 Un membro che non accedono ai dati di istanza non è contrassegnato come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Descrizione della regola  
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Per evitare un controllo in fase di esecuzione per ogni chiamata che consente di verifica che il puntatore all'oggetto corrente è diverso da null, la creazione di siti di chiamata non virtuali. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili delle prestazioni. In alcuni casi, l'errore per accedere all'istanza di oggetto corrente rappresenta un problema di correzione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Contrassegnare il membro come static (o condivise in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o utilizzare 'this' / 'Me' nel metodo corpo, se appropriato.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola per il codice fornito in precedenza per il quale la correzione sarebbe una modifica di rilievo.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)