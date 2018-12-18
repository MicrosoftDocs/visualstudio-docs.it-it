---
title: Creazione di un oggetto personalizzato di motore di Debug | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66ec73a13a3494ae6642e6d0f7397c9f3c1f0b0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-custom-debug-engine"></a>Creazione di un motore di Debug personalizzati
Un motore di debug (DE) è un componente che consente il debug di architetture in fase di esecuzione specifiche. È in genere solo un'implementazione DE per ogni ambiente di runtime.  
  
> [!NOTE]
>  Anche se sono presenti implementazioni DE separate per Transact-SQL e JScript, VBScript e JScript condividono un singolo DE.  
  
 Un Germania funziona con il sistema interprete o operazione per forniscono servizi di debug, come la valutazione di espressioni, i punti di interruzione e controllo di esecuzione. Questi servizi vengono implementati tramite le interfacce DE e possono causare il debugger per eseguire la transizione tra diverse modalità operative. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
 Creazione di un DE prevede i passaggi seguenti:  
  
1.  Registrazione di un DE con Visual Studio  
  
2.  Abilitazione di un programma da sottoporre a debug  
  
3.  Valutazione di controllo e lo stato di esecuzione  
  
4.  L'invio di eventi  
  
5.  Chiusura e disconnessione  
  
## <a name="in-this-section"></a>In questa sezione  
 [Registrazione di un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Illustra i passaggi necessari per registrare un motore di debug con Visual Studio in modo che può essere utilizzato.  
  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Viene illustrato che prima che la Germania può eseguire il debug di un programma, è innanzitutto necessario avviare la Germania o collegarlo a un programma esistente.  
  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Viene illustrato perché il debug di un'applicazione richiede l'implementazione della funzionalità di controllo di esecuzione.  
  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)  
 Viene illustrata la comunicazione tra il debugger e il DE come un modello di eventi in base a DCOM.  
  
 [Terminazione e scollegamento](../../extensibility/debugger/termination-and-detaching.md)  
 Viene illustrato come ottenere la terminazione normale, il che significa che non siano i punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug.  
  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)  
 Documenti di ordine di chiamata degli eventi che si verificano in una sessione di debug.  
  
 [Procedura: Eseguire il debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Viene illustrato come eseguire il debug di un DE personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)