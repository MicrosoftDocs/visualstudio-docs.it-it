---
title: Le impostazioni per le configurazioni di Debug c# del progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 054a015c5fcd6a70696ed6945faa5cbd01547168
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="project-settings-for--c-debug-configurations"></a>Impostazioni di progetto per le configurazioni di debug C#
È possibile modificare le impostazioni di progetto per una configurazione di debug c# nella **pagine delle proprietà** finestra, come descritto in [configurazioni Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). Le tabelle seguenti illustrano la posizione in cui sono disponibili le impostazioni correlate al debugger il **pagine delle proprietà** finestra.  
  
> [!WARNING]
>  Questo argomento non si applica alle app UWP. Vedere [avviare una sessione di debug (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a>Scheda Debug  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Configurazione**|Imposta la modalità per la compilazione dell'applicazione. Scegliere tra **attiva (Debug)**, **Debug**, **versione**, **tutte le configurazioni**.|  
|**Azione di avvio**|Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avviare il progetto** è l'impostazione predefinita e avvia il progetto di avvio per il debug. Per ulteriori informazioni, vedere [scelta del progetto di avvio](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Avvia programma esterno** consente di avviare e connettersi a un programma che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Per ulteriori informazioni, vedere [connessione a un programma in esecuzione](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web.|  
|**Argomenti della riga di comando**|Specifica gli argomenti della riga di comando per il programma da sottoporre a debug. Il nome del comando è il nome del programma specificato in Avvia programma esterno. Se l'opzione Azione di avvio è impostata su Avvia URL, non è possibile specificare gli argomenti della riga di comando.|  
|**Directory di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \bin\debug.|  
|**Usa computer remoto**|Il nome di un computer remoto in cui l'applicazione verrà eseguita ai fini del debug o [nome di server Msvsmon](../debugger/remote-debugging.md). Il percorso del file EXE sul computer remoto è specificato dalla proprietà Percorso output nella cartella Proprietà di configurazione, categoria Compila. Il percorso deve essere una directory condivisibile del computer remoto.|
|**Abilita debug codice non gestito**|Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso.|  
|**Abilita debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a>Scheda Compila  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**Simboli di compilazione condizionale:**|Le costanti DEBUG e TRACE vengono definite in questa posizione.<br /><br /> Esse attivano la compilazione condizionale del [classe Debug](/dotnet/api/system.diagnostics.debug) e [classe Trace](/dotnet/api/system.diagnostics.trace). Quando sono definite, eseguire il Debug e i metodi della classe Trace generano l'output per il [finestra di Output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br /> -Debug è generalmente definito nella versione di Debug di un programma e non definito nella versione di rilascio.<br />-Trace è generalmente definito nelle versioni di Debug e di rilascio.|  
|**Ottimizza codice**|Questa impostazione deve rimanere disattivata nella versione di debug, a meno che non venga rilevato un bug solo nel codice ottimizzato. L'esecuzione del debug di un codice ottimizzato è più complessa poiché le istruzioni non corrispondono direttamente alle istruzioni presenti nelle finestre del codice sorgente.|  
|**Percorso di output:**|Generalmente impostato su bin\Debug per l'esecuzione del debug.|

> [!NOTE]
> Per ulteriori informazioni sulle opzioni di debug trova nel **avanzate** pulsante, vedere [la finestra di dialogo Impostazioni di compilazione avanzate (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Il formato portabile per i file di simboli (PDB) è il più recente formato multipiattaforma per .NET Core. 
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)