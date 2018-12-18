---
title: Regole di prestazioni per l'utilizzo di .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ddfe3d7bdc4cb274a7b70dca48e45794d5f1cac
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="net-framework-usage-performance-rules"></a>Regole di prestazioni per l'utilizzo di .NET Framework
Le regole di prestazioni nella categoria relativa all'utilizzo di .NET Framework identificano metodi specifici ottimizzabili e modelli di utilizzo più generici, ad esempio Garbage Collection e conflitti di blocco, che possono essere analizzati per risolvere i problemi relativi alle prestazioni.  
  
|||  
|-|-|  
|[DA0001: Usare StringBuilder per le concatenazioni](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Le chiamate a <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> sono una percentuale significativa dei dati di profilatura. Considerare la possibilità di usare la classe <xref:System.Text.StringBuilder> per costruire stringhe da più segmenti.|  
|[DA0005: Raccolte GC2 frequenti](../profiling/da0005-frequent-gc2-collections.md)|Viene recuperato un numero relativamente elevato di oggetti di memoria .NET in Garbage Collection di generazione 2. Se Garbage Collection di generazione 1 contiene troppi oggetti di breve durata, il costo di gestione della memoria può diventare eccessivo.|  
|[DA0006: Eseguire l'override di Equals() per i tipi di valore](../profiling/da0006-override-equals-parens-for-value-types.md)|Le chiamate al metodo `Equals` o agli operatori di uguaglianza di un tipo di valore pubblico rappresentano una percentuale significativa dei dati di profilatura. Considerare la possibilità di implementare un metodo più efficiente.|  
|[DA0007: Evitare di usare eccezioni per il flusso di controllo](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Nei dati di profilatura è stato chiamato un numero elevato di gestori di eccezioni di .NET Framework. Considerare la possibilità di usare un'altra logica di flusso di controllo per ridurre il numero di eccezioni generate.|  
|[DA0010: Funzione GetHashCode dispendiosa](../profiling/da0010-expensive-gethashcode.md)|Le chiamate al metodo `GetHashCode` del tipo rappresentano una percentuale significativa dei dati di profilatura o la memoria viene allocata dal metodo `GetHashCode`. Ridurre la complessità del metodo.|  
|[DA0011: Funzione compareTo dispendiosa](../profiling/da0011-expensive-compareto.md)|Il metodo `CompareTo` del tipo è dispendioso o la memoria viene allocata dal metodo. Ridurre la complessità del metodo `CompareTo`.|  
|[DA0012: Uso elevato della reflection](../profiling/da0012-significant-amount-of-reflection.md)|Le chiamate a metodi <xref:System.Reflection?displayProperty=fullName> come <xref:System.Reflection.IReflect.InvokeMember%2A> e <xref:System.Reflection.IReflect.GetMember%2A> o ai metodi del tipo, ad esempio <xref:System.Type.InvokeMember%2A>, rappresentano una percentuale significativa dei dati di profilatura. Ove possibile considerare la possibilità di sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.|  
|[DA0013: Uso elevato di String.Split o String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Le chiamate ai metodi <xref:System.String.Split%2A?displayProperty=fullName> o <xref:System.String.Substring%2A> rappresentano una parte significativa dei dati di profilatura. È consigliabile usare <xref:System.String.IndexOf%2A> o <xref:System.String.IndexOfAny%2A> se si sta testando l'esistenza di una sottostringa in una stringa.|  
|[DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|I dati di sistema raccolti durante l'esecuzione della profilatura indicano che gli heap della memoria di .NET Framework hanno quasi raggiunto le dimensioni massime che gli heap gestiti possono avere in un processo a 32 bit. Considerare la possibilità di ripetere la profilatura usando il metodo di profilatura della memoria .NET e ottimizzando l'uso delle risorse gestite dall'applicazione.|  
|[DA0021: Frequenza elevata di Garbage Collection di generazione 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Viene recuperato un numero relativamente elevato di oggetti di memoria .NET in Garbage Collection di generazione 1. Se troppi oggetti di breve durata sono presenti in Garbage Collection di generazione 0, il costo di gestione della memoria può diventare eccessivo.|  
|[DA0022: Frequenza elevata di garbage collection di generazione 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Viene recuperato un numero elevato di oggetti di memoria .NET in Garbage Collection di generazione 2. Se Garbage Collection di generazione 1 contiene troppi oggetti di breve durata, il costo di gestione della memoria può diventare eccessivo. Questa regola viene attivata quando la frequenza di conflitti di blocco supera il valore di soglia superiore della regola DA0005.|  
|[DA0023: Tempo CPU GC elevato](../profiling/da0023-high-gc-cpu-time.md)|I dati sulle prestazioni del sistema raccolti durante la profilatura indicano che il tempo impiegato in Garbage Collection è elevato rispetto al tempo di elaborazione totale dell'applicazione.|  
|[DA0024: Tempo CPU GC eccessivo](../profiling/da0024-excessive-gc-cpu-time.md)|I dati sulle prestazioni del sistema raccolti durante la profilatura indicano che il tempo impiegato in Garbage Collection è eccessivamente elevato rispetto al tempo di elaborazione totale dell'applicazione. Questa regola viene attivata quando il tempo impiegato in Garbage Collection supera il valore di soglia superiore della regola DA0023.|  
|[DA0038: Frequenza elevata di conflitti di blocco](../profiling/da0038-high-rate-of-lock-contentions.md)|I dati sulle prestazioni del sistema raccolti con i dati di profilatura indicano una frequenza significativamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione. Considerare la possibilità di ripetere la profilatura usando il metodo di profilatura della concorrenza per individuare la causa dei conflitti.|  
|[DA0039: Frequenza molto elevata di conflitti di blocco](../profiling/da0039-very-high-rate-of-lock-contentions.md)|I dati sulle prestazioni del sistema raccolti con i dati di profilatura indicano una frequenza eccessivamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione. Considerare la possibilità di ripetere la profilatura usando il metodo di profilatura della concorrenza per individuare la causa dei conflitti. Questa regola viene attivata quando la frequenza di conflitti di blocco supera il valore di soglia superiore della regola DA0038.|