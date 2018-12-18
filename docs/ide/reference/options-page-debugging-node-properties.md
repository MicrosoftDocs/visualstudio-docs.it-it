---
title: "Pagina delle opzioni, Proprietà del nodo Debug | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 690eb875b0b9251dddcb36c4ad7ded17c36b67cb
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="options-page-debugging-node-properties"></a>Pagina delle opzioni, proprietà del nodo Debug
Le tabelle seguenti descrivono le pagine, o raccolte di proprietà, associate alla categoria **Debug**, `DTE.Properties("Debugging", <Property Page>)` della finestra di dialogo **Opzioni**.  
  
## <a name="general"></a>Generale  
 `DTE.Properties("Debugging", "General")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|PromptOnBreakpointDelete|Get/Set (Boolean)|Determina se il debugger richiede l'autorizzazione prima di eliminare tutti i punti di interruzione in un progetto.|  
|BreakAllProcesses|Get/Set (Boolean)|Determina se il debugger interrompe tutti i processi ogni volta che un singolo processo si interrompe.|  
|BreakAtBoundaries|Get/Set (Boolean)|Determina se il debugger interrompe l'esecuzione quando un'eccezione supera un limite tra AppDomain o tra codice gestito e codice nativo.|  
|EnableAddressLevelDebugging|Get/Set (Boolean)|Determina se sono abilitate le funzionalità di debug a livello di indirizzo.|  
|ShowDisassemblyIfNoSource|Get/Set (Boolean)|Determina se il debugger visualizza codice disassembly quando non è disponibile codice sorgente.|  
|EnableBreakpointFilters|Get/Set (Boolean)|Determina se il filtro dei punti di interruzione è abilitato.|  
|EnableExceptionAssistant|Get/Set (Boolean)|Determina se le informazioni sulle eccezioni vengono usate per le eccezioni gestite.|  
|UnwindCallstack|Get/Set (Boolean)|Determina se il debugger rimuove lo stack di chiamate per un'eccezione non gestita.|  
|EnableJustMyCode|Get/Set (Boolean)|Determina se Just My Code è attivato per C# e per il codice Visual Basic.|  
|ShowAllMembers|Get/Set (Boolean)|Per gli oggetti non utente, determina se il debugger visualizza tutti i membri degli oggetti nelle finestre delle variabili. Questa opzione ha effetto solo se Just My Code è abilitato.|  
|WarnIfNoUserCode|Get/Set (Boolean)|Determina se il debugger genera un avviso quando l'utente tenta di connettersi a un processo che non include il codice utente. Questa opzione ha effetto solo se Just My Code è abilitato.|  
|EnablePropertyEvaluation|Get/Set (Boolean)|Determina se il debugger valuta automaticamente le proprietà e le chiamate a funzioni implicite nel codice gestito.|  
|CallStringConversion|Get/Set (Boolean)|Determina se il debugger chiama in modo implicito una funzione di conversione delle stringhe su oggetti nelle finestre delle variabili.|  
|EnableSourceServer|Get/Set (Boolean)|Determina se il debugger può accedere al codice da un server di origine.|  
|PrintSourceServerDiagnostics|Get/Set (Boolean)|Determina se nella finestra di output vengono visualizzati messaggi diagnostici relativi al server di origine. Questa opzione non ha alcun effetto a meno che non sia abilitato l'accesso al server di origine.|  
|HighlightEntireLine|Get/Set (Boolean)|Determina se il debugger evidenzia un'intera riga per i punti di interruzione e l'istruzione corrente.|  
|RequireSourceToMatch|Get/Set (Boolean)|Determina se il debugger richiede che i file di origine corrispondano esattamente alla versione originale quando si aprono i file per il debug.|  
|RedirectOutputToImmediate|Get/Set (Boolean)|Determina se della finestra di output viene reindirizzata alla finestra di controllo immediato.|  
|ShowRawVariableStructure|Get/Set (Boolean)|Determina se gli oggetti nelle finestre delle variabili vengono visualizzati in formato non elaborato.|  
|SuppressJitOptimization|Get/Set (Boolean)|Per codice gestito, determina se l'ottimizzazione JIT viene eliminata dal debugger.|  
|WarnIfNoSymbols|Get/Set (Boolean)|Determina se il debugger visualizza un avviso se non sono disponibili simboli di debug quando viene avviato un processo.|  
|WarnIfScriptDisabled|Get/Set (Boolean)|Determina se il debugger visualizza un avviso se non è abilitato il debug di script quando viene avviato un processo.|  
|ShowMarkersForAllThreads|Get/Set (Boolean)|Determina se il debugger visualizza i marcatori dei thread.|  
|StepOverPropertiesAndOperators|Get/Set (Boolean)|Specifica se eseguire le istruzioni/routine di proprietà e operatori solo nel codice gestito.|  
  
## <a name="edit-and-continue"></a>Modifica e continuazione  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|EnableEditAndContinue|Get/Set (Boolean)|Determina se è abilitata la funzionalità Modifica e continuazione. Questa opzione si applica a tutti i linguaggi che supportano Modifica e continuazione.|  
|InvokedByCommands|Get/Set (Boolean)|Determina se la funzionalità Modifica e continuazione applica automaticamente le modifiche al codice quando l'utente seleziona un comando di debug, ad esempio **Passaggio** o **Continua**. Questa opzione si applica solo al codice nativo.|  
|InvokedByCommandsAskFirst|Get/Set (Boolean)|Determina se la funzionalità Modifica e continuazione richiede all'utente l'autorizzazione per applicare il codice quando l'utente seleziona un comando di debug, ad esempio **Passaggio** o **Continua**. Questa opzione si applica solo al codice nativo.|  
|WarnAboutStaleCode|Get/Set (Boolean)|Determina se il debugger genera un messaggio di avviso quando Modifica e continuazione comporta l'esecuzione di codice non aggiornato. Questa opzione si applica solo al codice nativo.|  
|RelinkChangesOnStop|Get/Set (Short)|Determina se Visual Studio consente di ricollegare le modifiche al codice applicate da Modifica e continuazione al termine dell'esecuzione dell'applicazione. Questa opzione si applica solo al codice nativo.|  
|AllowPrecompiling|Get/Set (Short)|Determina se alla funzionalità Modifica e continuazione è consentito caricare intestazioni precompilate in background. Questa opzione si applica solo al codice nativo.|  
  
## <a name="just-in-time"></a>JIT  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|JitManaged|Get/Set (Boolean)|Determina se il debug JIT è abilitato per il codice gestito.|  
|JitNative|Get/Set (Boolean)|Determina se il debug JIT è abilitato per il codice nativo.|  
|JitScript|Get/Set (Boolean)|Determina se il debug JIT è abilitato per il codice di script.|  
  
## <a name="native"></a>Nativo  
 `DTE.Properties("Debugging", "Native")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|LoadDllExports|Get/Set (Boolean)|Determina se il debugger carica le tabelle di esportazione DLL.|  
|EnableRPC|Get/Set (Boolean)|Determina se il debugger è in grado di eseguire istruzioni per le chiamate a procedure remote (RPC) COM.|  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo delle impostazioni relative alle opzioni](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Pagina delle opzioni, Proprietà del nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md)   
 [Modifica e continuazione, Debug, finestra di dialogo Opzioni](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)   
 [JIT, Debug, Finestra di dialogo Opzioni](../../debugger/just-in-time-debugging-options-dialog-box.md)