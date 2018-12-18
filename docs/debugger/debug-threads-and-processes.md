---
title: Strumenti per eseguire il debug di thread e processi | Documenti Microsoft
ms.custom: 
ms.date: 04/21/2017
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
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e6c6c8c239d27952c35486be308e5947aff50952
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Strumenti per eseguire il debug di thread e processi in Visual Studio
*Thread* e *processi* costituiscono concetti correlati in ambito informatico. Entrambi rappresentano infatti sequenze di istruzioni che devono essere eseguite in un ordine specifico. Le istruzioni incluse in thread o processi distinti possono tuttavia essere eseguite in parallelo.  
  
 I processi sono disponibili nel sistema operativo e corrispondono a ciò che gli utenti visualizzano sotto forma di programmi o applicazioni. I thread sono invece disponibili nei processi. Per questo motivo, i thread sono dette *processi leggeri*. Ciascun processo è costituito da uno o più thread.  
  
 La presenza di più processi consente a un computer di eseguire più attività contemporaneamente. La presenza di più thread consente invece a un processo di suddividere le operazioni da eseguire in parallelo. In un computer con più processori, i processi o i thread possono essere eseguiti in processori diversi consentendo l'effettiva elaborazione in parallelo.  
  
 Una perfetta elaborazione in parallelo non è sempre possibile. È talvolta necessario sincronizzare i thread. È inoltre possibile che un thread debba attendere un risultato di un altro thread o disporre di accesso esclusivo a una risorsa utilizzata da un altro thread. I problemi di sincronizzazione costituiscono una causa comune di bug in applicazioni con multithreading. È talvolta possibile che i thread rimangano in attesa di una risorsa che non diviene mai disponibile, Di conseguenza, una condizione denominata *deadlock*.  
  
 Nel debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono disponibili strumenti efficaci e di facile utilizzo per il debug di thread e processi.  
  
## <a name="tools-and-features"></a>Strumenti e funzionalità
Gli strumenti necessari per utilizzare in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dipendono dal tipo di codice si sta tentando di eseguire il debug:

- Per i processi, i principali strumenti sono il **Connetti a processo** nella finestra di dialogo di **processi** finestra e **posizione di Debug** barra degli strumenti.

- Per i thread sono i principali strumenti per il debug dei thread di **thread** (finestra), gli indicatori dei thread nelle finestre di origine, **stack in parallelo** finestra **espressioni di controllo parallelo** finestra e il **posizione di Debug** barra degli strumenti.  
  
- Per il codice che utilizza il <xref:System.Threading.Tasks.Task> nel [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/) (codice nativo), i principali strumenti per il debug di applicazioni multithreading sono le **Stack in parallelo** finestra il **espressioni di controllo parallelo** finestra e **attività** finestra (il **attività** supporta anche la finestra di Oggetto di promise JavaScript).

- Per il debug di thread nella GPU, lo strumento principale è il **thread GPU** windows.  
  
 Nella tabella riportata di seguito sono illustrate le informazioni disponibili e le operazioni che è possibile eseguire con ciascuno strumento:  
  
|Interfaccia utente|Informazioni disponibili|Operazioni eseguibili|  
|--------------------|---------------------------|-----------------------------|  
|**Connetti a processo** la finestra di dialogo|Processi disponibili cui è possibile eseguire la connessione:<br /><br /> -Nome process (.exe)<br />-Numero di ID processi<br />-Barra dei menu titolo<br />-Tipo (Managed v 4.0; Managed v 2.0, v 1.1, v 1.0; x86; x64; IA64)<br />-Nome utente (nome di account)<br />-Numero di sessione|Selezione di un processo a cui connettersi<br /><br /> Selezione di un computer remoto<br /><br /> Modifica del tipo di trasporto per la connessione a computer remoti|  
|**Processi** finestra|Processi collegati:<br /><br /> : Nome processo<br />-Numero di ID processi<br />-Path per elaborare .exe<br />-Barra dei menu titolo<br />-Stato (Interrompi. In esecuzione)<br />-Debug (nativo, gestito e così via.)<br />-Tipo di trasporto (predefinito, nativo senza autenticazione)<br />-Il qualificatore di trasporto (computer remoto)|Strumenti:<br /><br /> -Collegamento<br />-Scollegamento<br />-Termina<br /><br /> Menu di scelta rapida:<br /><br /> -Collegamento<br />-Scollegamento<br />-Disconnetti al termine del debug<br />-Termina|  
|**Thread** finestra|Thread nel processo corrente:<br /><br /> -ID thread<br />-ID gestito<br />-Categoria (thread principale, thread dell'interfaccia, gestore delle chiamate a procedura remota o thread di lavoro)<br />-Nome thread<br />-Location in cui viene creato thread<br />-Priorità<br />: Maschera di affinità<br />-Numero sospesi<br />: Nome processo<br />-Indicatore flag<br />-Indicatore sospeso|Strumenti:<br /><br /> -Ricerca<br />-Ricerca Stack di chiamate<br />-Contrassegna Just My Code<br />-Contrassegna selezione moduli personalizzata<br />-Raggruppa per<br />-Colonne<br />-Espandi/Comprimi stack di chiamate<br />-Espandere/comprimere gruppi<br />-Blocca/Sblocca thread<br /><br /> Menu di scelta rapida:<br /><br /> -Mostra thread nell'origine<br />-Passa al thread<br />-Blocca un thread in esecuzione<br />-Sblocca un thread bloccato<br />-Imposta flag del thread per Studio aggiuntivo<br />-Rimuovi flag del thread<br />-Rinomina thread<br />-Mostra / Nascondi thread<br /><br /> Altre azioni:<br /><br /> : Consente di visualizzare lo stack di chiamate per un thread in un suggerimento dati|  
|Finestra di origine|Gli indicatori dei thread all'estrema sinistra indicano thread singoli o più thread (disattivato per impostazione predefinita, attivata usando il menu di scelta rapida in **thread** finestra)|Menu di scelta rapida:<br /><br /> -Passa al thread<br />-Imposta flag del thread per Studio aggiuntivo<br />-Rimuovi flag del thread|  
|**Posizione di debug** barra degli strumenti|-Processo corrente<br />-Consente di sospendere l'applicazione<br />-Riprendi l'applicazione<br />-Consente di sospendere e arrestare l'applicazione<br />-Thread corrente<br />-Attivare o disattivare lo stato di flag di thread corrente<br />-Mostra solo thread con flag<br />-Mostra solo processo corrente<br />-Stack frame corrente|-Passa a un altro processo<br />-Consente di sospendere, riprendere o arrestare l'applicazione<br />-Passare a un altro thread nel processo corrente<br />-Passare a un altro stack frame del thread corrente<br />-Contrassegnare o rimuovere i flag dei thread correnti<br />-Mostra solo thread con flag<br />-Mostra solo processo corrente|  
|**Stack in parallelo** finestra|-Stack di chiamate per più thread in una finestra.<br />-Stack frame attivo per ogni thread.<br />-I chiamanti e chiamati per ogni metodo.|-Filtro thread specificati<br />-Passare alla visualizzazione attività<br />-Consente di contrassegnare o rimuovere un thread<br />-Zoom|   
|**Espressioni di controllo parallelo** finestra|-La colonna flag, nella quale è possibile contrassegnare un thread che si desidera prestare particolare attenzione.<br />-La colonna frame, in cui una freccia indica il frame selezionato.<br />-Colonna configurabile che consente di visualizzare il computer, processo, riquadro, attività e thread.|-Consente di contrassegnare o rimuovere un thread<br />-Visualizza solo thread con flag<br />-Frame opzione<br />-Consente di ordinare una colonna<br />-Thread gruppo<br />-Blocca o Sblocca i thread<br />-esportare i dati nella finestra Espressioni di controllo parallelo| 
|**Attività** finestra|-Consente di visualizzare informazioni sui <xref:System.Threading.Tasks.Task> oggetti inclusi ID attività, lo stato delle attività (programmato, in esecuzione, in attesa, in deadlock) e il thread assegnato all'attività.<br />-Percorso corrente nello stack di chiamate.<br />-Delegato passato all'attività al momento della creazione|-Passare all'attività corrente<br />-Consente di contrassegnare o rimuovere un'attività<br />-Consente di bloccare o sbloccare un'attività|  
|**Thread GPU** finestra|-La colonna flag, nella quale è possibile contrassegnare un thread che si desidera prestare particolare attenzione.<br />-Thread colonna corrente, in cui una freccia gialla indica che il thread corrente.<br />-La **conteggio Thread** colonna, che visualizza il numero di thread nella stessa posizione.<br />-La **riga** colonna, che consente di visualizzare la riga di codice in cui si trova ciascun gruppo di thread.<br />-La **indirizzo** colonna, che visualizza l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread.<br />-La **percorso** colonna, ovvero la posizione nel codice dell'indirizzo.<br />-La **stato** colonna, che indica se il thread è attivo o bloccato.<br />-La **riquadro** colonna, che indica l'indice della sezione per i thread nella riga.|-Modifica a un altro thread<br />-Consente di visualizzare un riquadro specifico e thread<br />-Consente di visualizzare o nascondere una colonna<br />-Ordina per colonna<br />-Thread gruppo<br />-Blocca o Sblocca i thread<br />-Consente di contrassegnare o rimuovere un thread<br />-Visualizza solo thread con flag|  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice GPU](../debugger/debugging-gpu-code.md)