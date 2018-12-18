---
title: Scheda Generale, finestra di dialogo proprietà Thread | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe6eb87418671b9b070aebaf60d1bb9c84b3623a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-thread-properties-dialog-box"></a>Scheda Generale, finestra di dialogo Proprietà thread
Utilizzare questa finestra di dialogo per ottenere ulteriori informazioni su un thread specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo su un [visualizzazione thread](../debugger/threads-view.md) finestra oppure aprire [visualizzazione messaggi](../debugger/messages-view.md) ed espandere un messaggio. Selezionare qualsiasi nodo thread nell'albero, quindi scegliere **proprietà** dal **vista** menu.  
  
 Il **proprietà Thread** la finestra di dialogo contiene un riquadro, il **generale** scheda. Sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Nome modulo**|Nome del modulo.|  
|**ID thread**|ID univoco di questo thread. Si noti che i numeri di ID thread vengono riutilizzati; consentono di identificare un thread solo per la durata del thread.|  
|**ID processo**|ID univoco di questo processo. Numeri di ID di processo vengono riutilizzati e identificano un processo solo per la durata del processo. Il tipo di oggetto processo viene creato quando viene eseguito un programma. Tutti i thread in un processo condividono lo stesso spazio di indirizzi e hanno accesso agli stessi dati. Scegliere questo valore per visualizzare le proprietà dell'ID di processo.|  
|**Lo stato del thread**|Lo stato corrente del thread. Un thread in esecuzione con un processore; un thread di Standby sta per farlo. È in attesa di un Thread pronto per utilizzare un processore perché non è disponibile. Un thread in fase di transizione è in attesa per una risorsa da eseguire, ad esempio l'attesa per il relativo stack di esecuzione di paging dal disco. Un thread in attesa non è necessario il processore perché è in attesa di completare un'operazione esterna o una risorsa diventi disponibile.|  
|**Motivo di attesa**|Questa opzione è disponibile solo quando il thread è nello stato di attesa. Coppie di eventi vengono utilizzate per comunicare con i sottosistemi protetti.|  
|**Tempo di CPU**|Tempo CPU totale utilizzato su questo processo e i relativi thread. Uguale al tempo utente + tempo privilegiato.|  
|**Tempo utente**|Tempo trascorso totale, che il thread ha impiegato per l'esecuzione del codice in modalità utente. Le applicazioni eseguite in modalità utente, i sottosistemi quali la gestione di finestre e il motore della grafica.|  
|**Tempo privilegiato**|Tempo trascorso totale, che il thread ha impiegato per l'esecuzione del codice in modalità privilegiata. Quando viene chiamato un servizio di sistema di Windows, il servizio verrà eseguito spesso in modalità privilegiata per accedere ai dati privati di sistema. Tali dati vengono protetti dall'accesso da thread in esecuzione in modalità utente. Chiamate al sistema possono essere esplicite o implicite, ad esempio quando si verifica un errore di pagina o un'interruzione.|  
|**Tempo trascorso**|Il tempo totale trascorso, in secondi, il thread è in esecuzione.|  
|**Priorità corrente**|La priorità dinamica corrente di questo thread. Thread all'interno di un processo può aumentare e ridurre le proprie priorità di base rispetto alla priorità del processo di base.|  
|**Priorità di base**|La priorità di base corrente del thread.|  
|**Indirizzo iniziale**|Indirizzo virtuale iniziale per il thread.|  
|**Utente PC**|Il contatore di programma utente per il thread.|  
|**Commutazioni di contesto**|Il numero di parametri da un thread a altro. Opzioni di thread possono verificarsi all'interno di un singolo processo o tra processi. Un commutatore di thread potrebbe dipendere da un thread di richiesta di informazioni o da un thread quando un thread con priorità maggiore diventa pronto per l'esecuzione.|