---
title: Scheda memoria, finestra di dialogo Proprietà processo | Microsoft Docs
description: Utilizzare la scheda memoria delle proprietà del processo per visualizzare il modo in cui un processo utilizza la memoria. Sono disponibili informazioni sullo spazio usato, lo spazio condiviso e lo spazio virtuale usato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a1bf0409dacdd6cb2f7de65462f637124a5cecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845022"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Scheda Memoria, finestra di dialogo Proprietà processo
Utilizzare la scheda **memoria** per visualizzare il modo in cui un processo utilizza la memoria. Per visualizzare la finestra di [dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo in una finestra [visualizzazione processi](../debugger/processes-view.md) . Selezionare un nodo di processo nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **memoria** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Virtual Bytes**|Dimensioni correnti, in byte, dello spazio degli indirizzi virtuali usato dal processo. L'utilizzo dello spazio degli indirizzi virtuali non implica necessariamente l'utilizzo corrispondente di pagine del disco o della memoria principale. Tuttavia, lo spazio virtuale è finito e l'uso di un numero troppo elevato può limitare la capacità del processo di caricare le librerie.|
|**N. massimo byte virtuali**|Il numero massimo di byte di spazio degli indirizzi virtuali usato dal processo in un momento specifico.|
|**Working Set**|Il set di pagine di memoria interessate di recente dai thread del processo. Se la memoria disponibile nel computer supera la soglia specificata, le pagine verranno lasciate nel working set di un processo anche se non sono utilizzate. Quando la memoria disponibile scende al di sotto di una soglia, le pagine vengono rimosse dal working set. Se sono necessari, verranno richiamati temporaneamente nel working set prima di lasciare la memoria principale.|
|**Working Set massimo**|Numero massimo di pagine del working set di questo processo in qualsiasi momento.|
|**Byte riserva di paging**|Quantità corrente di pool di paging che il processo ha allocato. Il pool di paging è un'area di memoria di sistema in cui i componenti del sistema operativo acquisiscono spazio quando eseguono le attività designate. Le pagine del pool di paging possono essere inserite nel file di paging quando il sistema non accede al sistema per periodi di tempo prolungati.|
|**Byte riserva non di paging**|Numero corrente di byte nel pool non di paging allocato dal processo. Il pool non di paging è un'area di memoria di sistema in cui lo spazio viene acquisito dai componenti del sistema operativo quando eseguono le attività designate. Non è possibile eseguire il paging delle pagine del pool non di paging nel file di paging; rimangono nella memoria principale fino a quando vengono allocati.|
|**Private Bytes**|Numero corrente di byte allocati da questo processo che non possono essere condivisi con altri processi.|
|**Byte disponibili**|Lo spazio degli indirizzi virtuali non utilizzati totale di questo processo.|
|**Byte riservati**|Quantità totale di memoria virtuale riservata per l'utilizzo futuro da parte di questo processo.|
|**Byte immagine liberi**|Quantità di spazio degli indirizzi virtuali non in uso o riservata da immagini all'interno di questo processo.|
|**Byte immagine riservati**|Somma di tutta la memoria virtuale riservata dalle immagini eseguite in questo processo.|