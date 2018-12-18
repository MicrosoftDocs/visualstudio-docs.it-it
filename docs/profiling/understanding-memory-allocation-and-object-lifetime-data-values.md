---
title: Informazioni sull'allocazione di memoria e i valori dei dati di durata di un oggetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b7569b36b954553dbb03e8a3934c375012a4349
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Informazioni sull'allocazione di memoria e i valori dei dati di durata di un oggetto

Il metodo di profilatura *Allocazione della memoria .NET* degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raccoglie informazioni sulle dimensioni e sul numero degli oggetti che sono stati creati in un'allocazione o eliminati in una Garbage Collection e informazioni aggiuntive sullo *stack di chiamate* della funzione quando si è verificato l'evento. Lo *stack di chiamate* è una struttura dinamica che archivia informazioni sulle funzioni in esecuzione nel processore.

Il profiler della memoria interrompe il processore del computer a ogni allocazione di un oggetto .NET Framework in un'applicazione sottoposta a profilatura. Quando vengono raccolti anche dati sulla durata degli oggetti, il profiler interrompe il processore dopo ogni operazione di Garbage Collection di .NET Framework. I dati vengono aggregati per ogni funzione profilata e per ogni tipo di oggetto.

## <a name="allocation-data"></a>Dati sull'allocazione

Quando si verifica un evento .memory, i conteggi e le dimensioni totali degli oggetti di memoria allocati o eliminati vengono incrementati.

Quando si verifica un evento di allocazione .memory, il profiler incrementa i conteggi dei campioni per ogni funzione nello stack di chiamate. Quando i dati vengono raccolti, solo una funzione nello stack di chiamate esegue il codice nel corpo della funzione. Le altre funzioni nello stack sono elementi padre nella gerarchia delle chiamate di funzioni che sono in attesa dei valori restituiti dalle funzioni che hanno chiamato.

- Per l'evento di allocazione, il profiler incrementa il conteggio dei campioni *esclusivi* della funzione che sta attualmente eseguendo le proprie istruzioni. Dato che un campione esclusivo fa anche parte del totale (*inclusivo*) dei campioni della funzione, viene incrementato anche il conteggio dei campioni inclusivi della funzione attiva.

- Il profiler incrementa il numero di campioni inclusivi di tutte le altre funzioni nello stack di chiamate.

## <a name="lifetime-data"></a>Dati sulla durata

Il Garbage Collector di .NET Framework gestisce l'allocazione e il rilascio di memoria per l'applicazione. Per ottimizzare le prestazioni del Garbage Collector, l'heap gestito è diviso in tre generazioni: 0, 1 e 2. Il Garbage Collector del runtime archivia i nuovi oggetti nella generazione 0. Gli oggetti non raccolti vengono promossi e archiviati nelle generazioni 1 e 2.

Il Garbage Collector recupera memoria tramite la deallocazione di un'intera generazione di oggetti. Per gli oggetti creati dall'applicazione sottoposta a profilatura, la visualizzazione Durata oggetti mostra il numero e le dimensioni degli oggetti e la generazione in cui vengono recuperati.