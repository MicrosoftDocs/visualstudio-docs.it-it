---
title: 'CA2207: Inizializzare i campi statici del tipo di valore inline | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 248a43284dbdb376adaa3712f66b349f2fb6ca2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inizializzare i campi statici dei tipi di valore inline
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un tipo di valore dichiara un costruttore statico esplicito.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando viene dichiarato un tipo di valore, viene sottoposto a un'inizializzazione predefinita in tutti i campi di tipo di valore sono impostati su zero e tutti i campi di tipo di riferimento sono impostati su `null` (`Nothing` in Visual Basic). Un costruttore statico esplicito è garantito solo da eseguire prima di un costruttore di istanza o viene chiamato un membro statico del tipo. Pertanto, se il tipo viene creato senza chiamare un costruttore di istanza, il costruttore statico non è garantito per l'esecuzione.  
  
 Se tutti i dati statici vengono inizializzati inline e non viene dichiarato alcun costruttore statico esplicito, i compilatori c# e Visual Basic aggiungono la `beforefieldinit` flag per la definizione di classe MSIL. Inoltre, i compilatori di aggiungono un costruttore statico privato che contiene il codice di inizializzazione statica. Questo costruttore statico privato è garantito da eseguire prima tutti i campi statici del tipo sono accessibili.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando viene dichiarato e rimuovere il costruttore statico.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)