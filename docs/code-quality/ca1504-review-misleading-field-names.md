---
title: 'CA1504: Controllare i nomi dei campi fuorvianti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc1317380eab4a63a7c60557fbec258485768885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Controllare i nomi dei campi fuorvianti
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Il nome di un campo di istanza inizia con "s _" o il nome di un `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo inizia con "m _".  
  
## <a name="rule-description"></a>Descrizione della regola  
 I nomi dei campi che iniziano con "s _" sono associati a dati statici da molti utenti. Analogamente, i nomi dei campi che iniziano con "m _" sono associati ai dati di istanza (membro). Per semplificare la gestione del codice, i nomi devono seguire le convenzioni utilizzate in genere.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il campo utilizzando il prefisso appropriato. In alternativa, in modo che il campo conforme al suffisso corrente aggiungendo o rimuovendo il `static` modificatore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.