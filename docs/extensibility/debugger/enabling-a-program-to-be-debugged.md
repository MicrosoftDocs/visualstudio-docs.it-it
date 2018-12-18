---
title: Abilitazione di un programma da sottoporre a debug | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a581c5a9ae56f52727c011db1de2ad35a5ba3592
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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
  
 [Collegamento di avvio basato su](../../extensibility/debugger/launch-based-attachment.md)  
 Viene descritto basato su avvio allegato a un programma, che risulta automatico all'avvio dal suo SDM.  
  
 [Invio degli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)  
 I passaggi per gli eventi richiesti durante la creazione di un motore di debug (DE) e collegarlo a un programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definisce un motore di debug (DE) e vengono descritti i servizi implementati tramite le interfacce DE e come possono causare il debugger per eseguire la transizione tra diverse modalità operative.