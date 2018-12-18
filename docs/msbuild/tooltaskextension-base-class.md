---
title: Classe di base ToolTaskExtension | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01d2abbed85b891378b0a9d5c4a41029bdc46cf3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="tooltaskextension-base-class"></a>Classe di base ToolTaskExtension
Molte attività ereditano dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension> che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Questa catena di ereditarietà aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella seguente vengono descritti i parametri delle classi di base.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine2> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.<br /><br /> Questa è una proprietà che consente agli autori di attività che ereditano da questa classe di non dovere eseguire il cast da `IBuildEngine` a `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine3> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione fornita dall'host.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|Parametro `bool` facoltativo.<br /><br /> Se impostata su `true`, questa attività passa **/Q** alla riga di comando di cmd.exe in modo che la riga di comando non venga copiata in stdout.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|Parametro di matrice `String` facoltativo.<br /><br /> Matrice di coppie di variabili di ambiente, separate da segni di uguale. Queste variabili vengono passate all'eseguibile generato in aggiunta a o con override selettivo del blocco di ambiente standard.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|Parametro di sola lettura di output `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito. Se l'attività ha registrato errori, ma il processo ha un codice di uscita pari a 0 (esito positivo), il parametro viene impostato su -1.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametro <xref:Microsoft.Build.Framework.ITaskHost> facoltativo.<br /><br /> Specifica l'istanza dell'oggetto host (può essere null). Il motore di compilazione imposta questa proprietà se l'IDE host ha associato un oggetto host a questa particolare attività.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|Parametro di sola lettura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facoltativo.<br /><br /> Ottiene un'istanza di una classe <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> che contiene metodi di registrazione delle attività.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Parametro `bool` facoltativo.<br /><br /> Se `true`, tutti i messaggi ricevuti nel flusso di errori standard vengono registrati come errori.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|Parametro `String` facoltativo.<br /><br /> Importanza con cui registrare il testo dal flusso di output standard.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|Parametro `String` facoltativo.<br /><br /> Importanza con cui registrare il testo dal flusso di output standard.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|Parametro virtuale `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, che indica che non esiste alcun periodo di timeout. Il timeout è espresso in millisecondi.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|Parametro virtuale `string` facoltativo.<br /><br /> I progetti possono implementarlo per eseguire l'override di un ToolName. Le attività possono eseguirne l'override per conservare il ToolName.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|Parametro `string` facoltativo.<br /><br /> Specifica la posizione da cui l'attività carica il file eseguibile sottostante. Se questo parametro viene omesso, l'attività usa il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|Parametro `bool` facoltativo.<br /><br /> Se `true`, questa attività crea un file batch per la riga di comando e lo esegue mediante il processore dei comandi anziché eseguire direttamente il comando.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|Parametro `bool` facoltativo.<br /><br /> Se `true`, questa attività restituisce il nodo quando l'attività è in esecuzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)