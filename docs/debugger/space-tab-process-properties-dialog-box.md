---
title: Scheda spazio, finestra di dialogo Proprietà processo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4b5a416c7d3eb466498e7cf4ff727134c0f20f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="space-tab-process-properties-dialog-box"></a>Scheda Spazio, finestra di dialogo Proprietà processo
Utilizzare il **spazio** scheda per esaminare lo spazio degli indirizzi di un processo. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo per un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **spazio** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Mostra per lo spazio di memoria**|Utilizzare questa casella di riepilogo per selezionare la categoria di spazio (immagine, il mapping, riservati o non assegnati).|  
|**Byte eseguibile**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzo che utilizza questo processo. File eseguibile è la memoria che può essere eseguita dai programmi, ma potrebbe non essere letto o scritta.|  
|**Byte Exec di sola lettura**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi in uso con le proprietà di sola lettura che utilizza questo processo. Exec di sola lettura è la memoria che può essere eseguita, nonché leggere.|  
|**Byte Exec-lettura / scrittura**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi in uso con le proprietà di lettura / scrittura che utilizza questo processo. Exec-lettura / scrittura è la memoria che può essere eseguita dai programmi, nonché leggere e modificata.|  
|**Byte di scrittura Exec copia**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi che può essere eseguita dai programmi nonché letti e scritto. Questo tipo di protezione viene utilizzato quando la memoria deve essere condivisa tra processi. Se i processi di condivisione lettura solo la memoria, quindi verrà utilizzata la stessa memoria. Se dei processi richiede l'accesso in scrittura, verrà effettuata una copia della memoria per il processo.|  
|**Byte non accessibili**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzo che impedisce l'uso di un processo. Una violazione di accesso viene generata se la scrittura o viene eseguito un tentativo di lettura.|  
|**Byte di sola lettura**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi che può essere eseguita, nonché leggere.|  
|**Byte di lettura / scrittura**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi che consente la lettura e scrittura.|  
|**Byte di scrittura-copia**|Per la categoria selezionata, la somma di tutto lo spazio di indirizzi che consente la condivisione della memoria per la lettura, ma non per la scrittura. Quando i processi leggono questa memoria, condividono la stessa memoria. Tuttavia, quando un processo di condivisione deve avere accesso in lettura/scrittura alla memoria condivisa, viene creata una copia di tale memoria per la scrittura.|