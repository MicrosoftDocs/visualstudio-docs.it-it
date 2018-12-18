---
title: Comandi di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4fc6746648e57903bd0da45bc15758b30a60801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-commands"></a>Comandi di Visual Studio
I comandi di Visual Studio consentono di richiamare un comando dalla finestra **Comando** , dalla finestra **Comando immediato** o dalla casella **Trova/Comando** . In ogni caso, per indicare che deve essere eseguito un comando anziché un'operazione di ricerca o di debug, viene usato il segno di maggiore (`>`).  
  
 È possibile trovare l'elenco completo dei comandi e la relativa sintassi nella finestra di dialogo **Opzioni** con le voci Tastiera, Ambiente selezionate.  
  
 Il carattere di escape per i comandi di Visual Studio è un accento circonflesso (^) con cui si indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo. In questo modo, è possibile incorporare virgolette diritte ("), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere letterale nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni. Ad esempio,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette. Se corrisponde all'ultimo carattere sulla riga, viene ignorato.  
  
 Nelle versioni localizzate dell'IDE, i nomi di comandi possono essere immessi sia nella lingua locale dell'IDE sia in lingua inglese. È possibile ad esempio digitare `File.NewFile` o `Fichier.NouveauFichier` nell'IDE francese per eseguire lo stesso comando.  
  
 A molti comandi sono associati alias. Per un elenco di alias di comando, vedere [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md).  
  
 I comandi seguenti accettano argomenti e/o opzioni.  
  
|Nome comando|Descrizione|  
|------------------|-----------------|  
|[Aggiungi elemento esistente](../../ide/reference/add-existing-item-command.md)|Aggiunge un file esistente alla soluzione corrente e lo apre.|  
|[Aggiungi progetto esistente](../../ide/reference/add-existing-project-command.md)|Aggiunge un progetto esistente alla soluzione corrente.|  
|[Aggiungi nuovo elemento](../../ide/reference/add-new-item-command.md)|Aggiunge un nuovo elemento, ad esempio un file con estensione htm, css o txt o una pagina con frame, alla soluzione corrente e lo apre.|  
|[Alias](../../ide/reference/alias-command.md)|Crea un nuovo alias per un comando completo, per un comando completo con i relativi argomenti oppure per un altro alias.|  
|[Valuta istruzione](../../ide/reference/evaluate-statement-command.md)|Valuta e visualizza l'istruzione specificata.|  
|[Find](../../ide/reference/find-command.md)|Ricerca il testo nei file usando un subset delle opzioni disponibili nel comando **Trova e sostituisci** .|  
|[Cerca nei file](../../ide/reference/find-in-files-command.md)|Ricerca il testo nei file usando un subset delle opzioni disponibili nel comando [Cerca nei file](../../ide/find-in-files.md).|  
|[Vai](../../ide/reference/go-to-command.md)|Sposta il cursore sulla riga specificata.|  
|[Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)|Visualizza lo stack di chiamate corrente.|  
|[Elenca disassembly](../../ide/reference/list-disassembly-command.md)|Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.|  
|[Elenca memoria](../../ide/reference/list-memory-command.md)|Visualizza il contenuto dell'intervallo di memoria specificato.|  
|[Elenca moduli](../../ide/reference/list-modules-command.md)|Elenca i moduli disponibili per il processo corrente.|  
|[Elenca registri](../../ide/reference/list-registers-command.md)|Visualizza un elenco di registri.|  
|[Elenca origine](../../ide/reference/list-source-command.md)|Visualizza le righe del codice sorgente specificate.|  
|[Elenca thread](../../ide/reference/list-threads-command.md)|Visualizza un elenco dei thread del programma corrente.|  
|[Registra output finestra di comando](../../ide/reference/log-command-window-output-command.md)|Copia interamente l'input e l'output della finestra di comando in un file.|  
|[Nuovo file](../../ide/reference/new-file-command.md)|Crea un nuovo file e lo aggiunge al progetto attualmente selezionato.|  
|[Apri file](../../ide/reference/open-file-command.md)|Apre un file esistente e consente di specificare un editor.|  
|[Apri progetto](../../ide/reference/open-project-command.md)|Apre un progetto esistente e consente di aggiungerlo alla soluzione corrente.|  
|[Apri soluzione](../../ide/reference/open-solution-command.md)|Apre una soluzione esistente.|  
|[Print](../../ide/reference/print-command.md)|Valuta l'espressione e visualizza i risultati o il testo specificato.|  
|[Comando Controllo immediato](../../ide/reference/quick-watch-command.md)|Visualizza il testo selezionato o specificato nel campo **Espressione** della finestra di dialogo **Espressione di controllo rapida** .|  
|[Sostituisci](../../ide/reference/replace-command.md)|Sostituisce elementi di testo nei file usando un subset delle opzioni disponibili nel comando **Trova e sostituisci** .|  
|[Sostituisci nei file](../../ide/reference/replace-in-files-command.md)|Sostituisce elementi di testo nei file usando un subset delle opzioni disponibili nella [Sostituisci nei file](../../ide/replace-in-files.md).|  
|[Imposta stack frame corrente](../../ide/reference/set-current-stack-frame-command.md)|Consente di visualizzare uno specifico stack frame.|  
|[Imposta thread corrente](../../ide/reference/set-current-thread-command.md)|Consente di visualizzare un thread specifico.|  
|[Imposta radice](../../ide/reference/set-radix-command.md)|Determina il numero di byte da visualizzare.|  
|[Shell](../../ide/reference/shell-command.md)|Avvia i programmi da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come se il comando venisse eseguito dal prompt dei comandi.|  
|[Comando ShowWebBrowser](../../ide/reference/showwebbrowser-command.md)|Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).|  
|[Start](../../ide/reference/start-command.md)|Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.|  
|[Path](../../ide/reference/symbol-path-command.md)|Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.|  
|[Attiva/disattiva punto di interruzione](../../ide/reference/toggle-breakpoint-command.md)|Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.|  
|[Comando Espressioni di controllo](../../ide/reference/watch-command.md)|Crea e apre un'istanza specificata di una finestra **Espressione di controllo** .|  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)