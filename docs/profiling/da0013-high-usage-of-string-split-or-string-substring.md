---
title: 'DA0013: Utilizzo elevato di String.Split o String.Substring | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: de4419e5d83630a09aa3caa2afcd2318266520bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Utilizzo elevato di String.Split/String.Substring
|||  
|-|-|  
|ID regola|DA0013|  
|Categoria|Guida all'uso di .NET Framework|  
|Metodi di profilatura|Campionamento|  
|Messaggio|Si consiglia di ridurre l'utilizzo delle funzioni String.Split e String.Substring.|  
|Tipo regola|Avviso|  
  
## <a name="cause"></a>Causa  
 Le chiamate ai metodi System.String.Split o System.String.Substring rappresentano una percentuale significativa dei dati di profilatura. È consigliabile usare System.String.IndexOf o System.String.IndexOfAny se si sta verificando l'esistenza di una sottostringa in una stringa.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il metodo Split agisce su un oggetto String e restituisce una nuova matrice di stringhe che contiene le sottostringhe dell'originale. La funzione alloca memoria per l'oggetto matrice restituito e alloca un nuovo oggetto String per ogni elemento della matrice trovato. Allo stesso modo, il metodo Substr agisce su un oggetto String e restituisce una nuova stringa equivalente alla sottostringa richiesta.  
  
 Se la gestione delle allocazioni di memoria è di importanza fondamentale nell'applicazione è consigliabile usare alternative ai metodi String.Split e String.Substr. Ad esempio, è possibile usare il metodo IndexOf o IndexOfAny per individuare una sottostringa specifica all'interno di una stringa di caratteri senza creare una nuova istanza della classe String.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilo di campionamento. Esaminare le funzioni chiamanti per trovare le sezioni del programma che fanno maggior uso dei metodi System.String.Split o System.String.Substr. Se possibile, usare il metodo IndexOf o IndexOfAny per individuare una sottostringa specifica all'interno di una stringa di caratteri senza creare una nuova istanza della classe String.