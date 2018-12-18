---
title: Scheda Generale, elaborare la finestra di dialogo proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà processo
Utilizzare il **generale** tab per ottenere ulteriori informazioni su un processo specifico. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo per un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Le impostazioni seguenti sono disponibili sul **generale** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome modulo**|Nome del modulo.|  
|**ID processo**|ID univoco di questo processo. Numeri di ID di processo vengono riutilizzati e identificano un processo solo per la durata del processo. Il tipo di oggetto processo viene creato quando viene eseguito un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati.|  
|**Valore Base di priorità**|La priorità di base corrente di questo processo. Thread all'interno di un processo può aumentare e ridurre le proprie priorità di base rispetto alla priorità di base del processo.|  
|**Thread**|Il numero di thread attualmente attivi nel processo corrente.|  
|**Tempo di CPU**|Tempo CPU totale utilizzato su questo processo e i relativi thread. Uguale all'ora di utente più tempo privilegiato.|  
|**Tempo utente**|Tempo cumulativo trascorso che thread del processo hanno impiegato per l'esecuzione del codice in modalità utente thread non inattivo. Le applicazioni eseguite in modalità utente, i sottosistemi, ad esempio la gestione di finestre e il motore della grafica.|  
|**Tempo privilegiato**|Il tempo totale trascorso questo processo è stato in esecuzione in modalità privilegiata in thread non inattivo. Il livello di servizio, le routine e il Kernel eseguite in modalità privilegiata. Driver di dispositivo per la maggior parte dei dispositivi diversi da schede video grafiche e le stampanti eseguire anche in modalità privilegiata. Alcune operazioni eseguite da Windows per l'applicazione possono apparire in altri processi di sottosistema oltre al tempo privilegiato.|  
|**Tempo trascorso**|Il tempo totale trascorso che questo processo è in esecuzione.|