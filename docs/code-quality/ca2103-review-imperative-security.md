---
title: 'CA2103: Controllare la sicurezza imperativa | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 051c94905e8d62d39ef837b6ef2520f345b8ca56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Controllare la sicurezza imperativa
|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo utilizza la sicurezza imperativa e potrebbe costruire l'autorizzazione tramite le informazioni sullo stato o i valori restituiti che possono essere modificati mentre la richiesta è attiva.  
  
## <a name="rule-description"></a>Descrizione della regola  
 La sicurezza imperativa utilizza oggetti gestiti per specificare le autorizzazioni e azioni di sicurezza durante l'esecuzione di codice, confrontato con la sicurezza dichiarativa, che utilizza attributi per archiviare le autorizzazioni e azioni nei metadati. La sicurezza imperativa è molto flessibile in quanto è possibile impostare lo stato di un oggetto di autorizzazione e selezionare le azioni di sicurezza con le informazioni che non sono disponibile in fase di esecuzione. Tale flessibilità comporta il rischio che le informazioni di runtime utilizzato per determinare che lo stato di un'autorizzazione non rimane invariate, purché l'azione è attiva.  
  
 Utilizzare la sicurezza dichiarativa quando possibile. Le richieste dichiarative sono più facili da comprendere.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rivedere le richieste di sicurezza imperativa per assicurarsi che lo stato dell'autorizzazione non si basa sulle informazioni che possono cambiare, purché l'autorizzazione è in uso.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se l'autorizzazione non si basa sulla modifica dei dati. Tuttavia, è preferibile modificare la richiesta imperativa nel relativo equivalente dichiarativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)   
 [Dati e modellazione](/dotnet/framework/data/index)