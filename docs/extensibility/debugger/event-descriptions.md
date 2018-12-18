---
title: Le descrizioni degli eventi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 600d9576d72dbd36b5ff7c2a0d9f0333f72dfafa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="event-descriptions"></a>Descrizioni degli eventi
Ogni tipo di evento con uno scopo specifico.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Gli eventi e i motivi per l'utilizzo  
  
|event|Descrizione|  
|-----------|-----------------|  
|Attivare gli eventi del documento|Si verifica quando il motore di debug (DE) richiede l'IDE di apertura o di un documento di portare in primo piano.|  
|Punto di interruzione associato o eventi di errore di punto di interruzione|Inviato quando è associato un punto di interruzione o non è possibile associare un punto di interruzione e viene restituito un errore.|  
|Eventi punto di interruzione non associato|Si verificano quando un punto di interruzione associato viene disassociata dal codice.|  
|Può arrestare eventi|Inviato all'IDE per determinare se l'utente desidera arrestare in un punto specificato nel codice.|  
|Eventi punto di interruzione|Si verifica quando viene raggiunto un punto di interruzione di dati o codice.|  
|Eventi testo del documento|Si verifica quando viene modificato il testo in un documento. Questi eventi non vengono inviati tramite il `IDebugEventCallBack2::Event` metodo.|  
|Motore di creazione di eventi|Inviato quando si crea un modulo di gestione.|  
|Eventi punto di ingresso|Inviato quando il programma in fase di debug ha eseguito il codice di inizializzazione e raggiunto il primo punto di ingresso utente.|  
|Eventi di eccezione|Inviato quando un programma in esecuzione raggiunge un'eccezione.|  
|Eventi di completamento valutazione di espressioni|Inviato quando la valutazione dell'espressione asincrona è stata completata.|  
|Trovare gli eventi di simbolo|Inviato ogni volta che la Germania dovrà chiedere all'utente di trovare i simboli per un modulo.|  
|Eventi di caricamento completati|Inviati solo quando il carico programma iniziale è stato completato e il primo codice sta per eseguire il programma.|  
|Eventi dei messaggi|Inviato quando i messaggi vengono inviati agli utenti.|  
|Eventi di caricamento moduli|Inviato quando un nuovo modulo viene caricato o scaricato.|  
|Eventi di stringa di output|Inviato quando il programma scrive l'output di debug.|  
|Creare e distruggere gli eventi|Invio di annunciare la creazione o la distruzione di thread, i programmi, proprietà, le sessioni e i processi in modo IDE di Visual Studio può tenere traccia dello stato dei programmi in corso il debug.|  
|Eventi di passaggio completati|Inviato quando un passaggio è stato completato.|  
|Eventi di modifica nome thread|Inviato quando l'utente modifica il nome di un thread.|  
|Eventi di modifica nome programma|Inviato quando l'utente modifica il nome di un programma.|  
  
## <a name="see-also"></a>Vedere anche  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)