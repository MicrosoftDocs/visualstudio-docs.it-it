---
title: 'Procedura: utilizzare il registro attività | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-activity-log"></a>Procedura: utilizzare il registro attività
Pacchetti VSPackage possono scrivere messaggi nel registro attività. Questa funzionalità è particolarmente utile per il debug di pacchetti VSPackage in ambienti di vendita al dettaglio.  
  
> [!TIP]
>  Il registro attività è sempre attivato. Visual Studio è possibile mantenere un buffer in sequenza le ultime 100 voci, nonché le prime 10 voci, che dispone di informazioni di configurazione generale.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività  
  
1.  Inserire il codice nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo o in qualsiasi altro metodo tranne che nel costruttore VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Il codice ottiene la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> del servizio e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Scrive una voce informativo nel log delle attività usando il contesto relative alla lingua corrente.  
  
2.  Quando il pacchetto VSPackage è caricato (in genere quando viene richiamato un comando o si apre una finestra), il testo venga scritto nel registro attività.  
  
### <a name="to-examine-the-activity-log"></a>Per esaminare il registro attività  
  
1.  Eseguire Visual Studio con il [Log/](../ide/reference/log-devenv-exe.md) opzione della riga di comando per scrivere il XML nel disco durante la sessione.

2.  Dopo la chiusura di Visual Studio, trovare il log attività nella sottocartella per i dati di Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.xml.  
  
3.  Aprire il registro attività con qualsiasi editor di testo. Di seguito è riportato una tipico voce:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Poiché il registro attività è un servizio, il registro attività non è disponibile nel costruttore VSPackage.  
  
 È necessario ottenere il registro attività appena prima di scrivere in esso. Non memorizzare nella cache o salvare il registro attività per un utilizzo futuro.  
  
## <a name="see-also"></a>Vedere anche
 [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Risoluzione dei problemi di VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
