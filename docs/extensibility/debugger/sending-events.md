---
title: L'invio di eventi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>L'invio di eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi in base a DCOM. Gli eventi vengono inviati come oggetti COM, e ogni evento dispone di parametri che specificano le operazioni seguenti:  
  
-   Germania che ha chiamato l'evento.  
  
-   Una descrizione di cosa è successo.  
  
-   Il processo, un programma e informazioni sul thread che identifica il contesto di in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un DE.  
  
-   Il tipo di evento che indica se l'evento è sincrono o asincrono.  
  
 Tutti gli eventi di debug vengono inviati utilizzando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Origini evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Vengono illustrati due origini di eventi: il motore di debug (DE) e la sessione di debug manager (SDM).  
  
 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md)  
 Vengono descritti i tipi di eventi attualmente supportate: sincroni e asincroni.  
  
 [Descrizioni di eventi](../../extensibility/debugger/event-descriptions.md)  
 Definisce gli eventi e i motivi per l'uso personale.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Viene descritto il funzionamento di un Germania con sistema operativo o interprete per fornire servizi di debug.