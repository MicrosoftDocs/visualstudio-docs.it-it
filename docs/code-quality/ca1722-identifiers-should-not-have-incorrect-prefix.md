---
title: 'CA1722: Gli identificatori non devono contenere il prefisso corretto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 141adcf6e21c7e0c8d737411988e73fbfbece805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Category|Microsoft. naming|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un identificatore ha un prefisso non corretto.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.  
  
 I nomi di tipo non dispone di un prefisso specifico e non devono essere preceduti da "C". Questa regola segnala violazioni per i nomi di tipo, ad esempio "CMyClass" e non segnala violazioni per i nomi dei tipi, ad esempio 'Cache'.  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere il prefisso dall'identificatore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)