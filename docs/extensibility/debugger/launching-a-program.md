---
title: Avvio di un programma | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="launching-a-program"></a>Un programma di avvio
Gli utenti che desiderano eseguire il debug di un programma è possono premere F5 per eseguire il debugger dall'IDE. Si inizia una serie di eventi che implicano l'IDE per la connessione a un motore di debug (DE), che a sua volta connesso, o collegato, per il programma come indicato di seguito:  
  
1.  L'IDE chiama innanzitutto il pacchetto del progetto per ottenere le impostazioni di debug di progetto attivo della soluzione. Le impostazioni includono la directory di avvio, le variabili di ambiente, la porta in cui verrà eseguito il programma e Germania da utilizzare per creare il programma, se specificato. Queste impostazioni vengono passate al pacchetto di debug.  
  
2.  Se viene specificato un Germania, la Germania chiama il sistema operativo per avviare il programma. Avvio del programma, di conseguenza l'ambiente in fase di esecuzione del programma viene caricato. Ad esempio, se un programma viene scritto in codice MSIL, common language runtime verrà richiamato per eseguire il programma.  
  
     oppure  
  
     Se non viene specificato un Germania, la porta chiama il sistema operativo per avviare il programma, causando l'ambiente in fase di esecuzione del programma da caricare.  
  
    > [!NOTE]
    >  Se un Germania viene utilizzato per avviare un programma, è probabile che la Germania stesso verrà collegato al programma.  
  
3.  A seconda che la Germania o la porta ha avviato il programma, la Germania o l'ambiente di runtime quindi crea una descrizione del programma, o un nodo e notifica la porta che il programma è in esecuzione.  
  
    > [!NOTE]
    >  È consigliabile che l'ambiente di runtime creare il nodo di programma, perché il nodo del programma è una rappresentazione leggera di un programma che è possibile eseguire il debug. Non è necessario per caricare un intero DE solo per creare e registrare un nodo di programma. Se la Germania è progettato per l'esecuzione in corso l'IDE, ma non IDE è effettivamente in esecuzione, è necessario utilizzare un componente che è possibile aggiungere un nodo di programma per la porta.  
  
 Il programma appena creato, insieme a eventuali altri programmi, correlati o non correlati, avviato o collegati per dall'IDE stesso, creare una sessione di debug.  
  
 A livello di codice quando l'utente prima di tutto preme **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]del pacchetto di debug chiama il pacchetto del progetto (che è associato il tipo di programma avviato) tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo, che a sua volta compila un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> struttura con impostazioni di debug della soluzione progetto attivo. Questa struttura viene passata al pacchetto di debug tramite una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metodo. Il pacchetto di debug crea quindi un'istanza di gestione di debug di sessione (SDM), che consente di avviare il programma da motori di debug in fase di debug e di eventuali oggetti associati.  
  
 Uno degli argomenti passati al SDM è il GUID della DE da utilizzare per avviare il programma.  
  
 Se non è il GUID DE `GUID_NULL`, il SDM creato la Germania e quindi chiama il relativo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo per avviare il programma. Ad esempio, se un programma viene scritto in codice nativo, quindi `IDebugEngineLaunch2::LaunchSuspended` probabilmente chiamerà `CreateProcess` e `ResumeThread` (funzioni Win32) per eseguire il programma.  
  
 Avvio del programma, di conseguenza l'ambiente in fase di esecuzione del programma viene caricato. La Germania o l'ambiente di runtime crea un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) per descrivere il programma di interfaccia e passa l'interfaccia a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) per notificare la porta che il programma è è in esecuzione.  
  
 Se `GUID_NULL` viene passato, quindi la porta avvia il programma. Quando il programma è in esecuzione, l'ambiente di runtime crea un `IDebugProgramNode2` interfaccia per descrivere il programma e lo passa al `IDebugPortNotify2::AddProgramNode`. Questa notifica la porta che il programma è in esecuzione. Quindi il SDM collega il motore di debug per il programma in esecuzione.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)  
 Viene illustrato cosa accade dopo un programma viene avviato e la porta di notifica.  
  
 [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documenti quando la sessione di debug è possibile collegare la Germania al programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a numerose attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.