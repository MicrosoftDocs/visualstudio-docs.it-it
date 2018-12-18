---
title: Abilitazione di un programma da sottoporre a debug | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f8dc37e5d59738e6ef326be71e773c1e4e57351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enabling-a-program-to-be-debugged"></a>Abilitazione di un programma da sottoporre a debug
Prima che il motore di debug (DE) può eseguire il debug di un programma, è necessario avviare la Germania o collegarlo a un programma esistente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)  
 Viene descritto come ottenere una porta come il primo passaggio per abilitare un programma da sottoporre a debug.  
  
 [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)  
 Viene illustrato il passaggio successivo all'attivazione di un programma da sottoporre a debug: registrazione con la porta. Una volta registrato, il programma di debug può essere eseguito tramite il processo di collegamento o il debug just-in-time (JIT).  
  
 [Collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md)  
 Viene illustrato il passaggio successivo: collegare il debugger al programma.  
  
 [Collegamento di avvio-based](../../extensibility/debugger/launch-based-attachment.md)  
 Viene descritto basato su avvio allegato a un programma, che risulta automatico all'avvio dal suo SDM.  
  
 [Invio degli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)  
 I passaggi per gli eventi richiesti durante la creazione di un motore di debug (DE) e collegarlo a un programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definisce un motore di debug (DE) e vengono descritti i servizi implementati tramite le interfacce DE e come possono causare il debugger per eseguire la transizione tra diverse modalità operative.