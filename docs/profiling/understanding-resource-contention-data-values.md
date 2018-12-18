---
title: Informazioni sui valori dei dati su conflitti di risorse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc41ee4c3c9f53d45245c6c305d7f8e221757f4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="understanding-resource-contention-data-values"></a>Informazioni sui valori dei dati su conflitti di risorse

La profilatura dei conflitti di risorse raccoglie informazioni dettagliate sullo stack di chiamate ogni volta che thread concorrenti in un'applicazione sono obbligati ad attendere l'accesso a una risorsa condivisa.

I report sui conflitti di risorse visualizzano il numero totale di conflitti e il tempo totale trascorso in attesa di una risorsa per i moduli, le funzioni, le righe del codice sorgente e le istruzioni in cui si è verificata l'attesa.

- I valori inclusivi mostrano il numero totale di conflitti che hanno costretto una funzione ad attendere a causa di conflitti di risorse e il tempo totale di attesa per la funzione.  I conflitti causati dalle funzioni figlio chiamate dalla funzione sono inclusi nei valori inclusivi.

- I valori esclusivi mostrano solo il numero di conflitti che hanno costretto una funzione ad attendere e che sono stati causati dal codice nel corpo della funzione. I conflitti causati da funzioni figlio non sono inclusi. Il tempo esclusivo per la funzione include inoltre solo i tempi di attesa causati dalle istruzioni nel corpo della funzione.

Le visualizzazioni dei report sui conflitti di risorse includono anche grafici della sequenza temporale che mostrano i singoli eventi di conflitto nel tempo e gli stack di chiamate che hanno creato l'evento specifico. Per altre informazioni, vedere uno degli argomenti seguenti:

- [Visualizzazione Dettagli thread](../profiling/thread-details-view-contention-data.md)

- [Visualizzazione Dettagli risorsa](../profiling/resource-details-view-contention-data.md)

Per altre informazioni sulla seconda modalità di profilatura della concorrenza, vedere [Visualizzatore di concorrenza](../profiling/concurrency-visualizer.md).