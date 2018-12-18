---
title: Opzioni, Editor di testo, C/C++, Avanzate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: b09c4421c5af79420023ccc4b659280c6bce33c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-cc-advanced"></a>Opzioni, Editor di testo, C/C++, Avanzate
Modificando queste opzioni è possibile modificare il comportamento correlato a IntelliSense e il database di esplorazione quando si programma in C o C++.  
  
 Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo** e **C/C++** e quindi fare clic su **Avanzate**.  
  
> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="browsingnavigation"></a>Esplorazione/Navigazione  
 È consigliabile non scegliere mai queste opzioni tranne nel raro caso in cui una soluzione sia talmente grande da richiedere all'attività del database il consumo di una quantità eccessiva di risorse di sistema.  
  
 **Disabilita database**  
 L'uso del database di esplorazione del codice (SDF), tutte le altre opzioni di esplorazione/navigazione e tutte le funzionalità di IntelliSense, ad eccezione del completamento automatico #include, sono disabilitati.  
  
 **Disabilita aggiornamenti database**  
 Il database verrà aperto in sola lettura e non verranno eseguiti aggiornamenti alla modifica dei file. La maggior parte delle funzionalità continuerà a funzionare. Quando tuttavia verranno apportate modifiche, i dati diventeranno obsoleti e si otterranno risultati non corretti.  
  
 **Disabilita aggiornamenti automatici del database**  
 Il database di esplorazione del codice non verrà aggiornato automaticamente alla modifica dei file di origine. Se tuttavia si apre **Esplora soluzioni**, si apre il menu di scelta rapida per il progetto e quindi si sceglie **Ripeti analisi soluzione**, tutti i file obsoleti verranno verificati e il database verrà aggiornato.  
  
 **Disabilita file impliciti**  
 Il database di esplorazione del codice non raccoglierà dati per i file non specificati in un progetto. Un progetto contiene file di origine e file di intestazione specificati in modo esplicito. I file impliciti sono inclusi dai file espliciti (ad esempio, afxwin.h, windows.h e atlbase.h). In genere, il sistema rileva questi file e li indicizza per diverse funzionalità di esplorazione (inclusa Passa a). Se si sceglie questa opzione, tali file non vengono indicizzati e alcune funzionalità non sono per loro disponibili. Se si sceglie questa opzione, vengono scelte in modo implicito anche "Disabilita pulizia implicita" e "Disabilita cartelle dipendenze esterne".  
  
 **Disabilita pulizia implicita**  
 Il database di esplorazione del codice non pulisce i file impliciti a cui non viene più fatto riferimento. Questa opzione impedisce la rimozione dei file impliciti dal database quando non vengono più usati. Ad esempio, se si aggiunge una direttiva `#include` che riconduce mapi.h a uno dei file di origine, mapi.h verrà trovato e indicizzato. Se in seguito si rimuove l'istruzione #include e al file non viene fatto riferimento altrove, le informazioni su di esso verranno infine rimosse a meno che non sia stata scelta questa opzione. (Vedere l'opzione **Ripeti analisi intervallo soluzione**.) Questa opzione viene ignorata quando si ripete in modo esplicito l'analisi della soluzione.  
  
 **Disabilita cartelle dipendenze esterne**  
 La cartella Dipendenze esterne per ogni progetto non viene creata o aggiornata. In **Esplora soluzioni** ogni progetto contiene una cartella Dipendenze esterne, che contiene tutti i file impliciti per il progetto. Se si sceglie questa opzione, tale cartella non viene visualizzata.  
  
 **Ricrea database**  
 Consente di ricreare da zero il database di esplorazione del codice la volta successiva che viene caricata la soluzione. Se si sceglie questa opzione, il database di esplorazione del codice viene cancellato al successivo caricamento della soluzione, provocando così la rigenerazione del database e l'indicizzazione di tutti i file.  
  
 **Ripeti analisi intervallo soluzione**  
 Viene pianificato un processo 'Ripeti analisi soluzione' per l'intervallo specificato. È necessario specificare tra 0 e 5000 minuti. Il valore predefinito è 60 minuti. Mentre viene ripetuta l'analisi della soluzione, i timestamp dei file vengono controllati per stabilire se un file sia stato modificato all'esterno dell'IDE. (Le modifiche apportate nell'IDE vengono rilevate automaticamente e i file vengono aggiornati.) I file inclusi in modo implicito vengono controllati per stabilire se vi si faccia ancora riferimento.  
  
## <a name="diagnostic-logging"></a>Registrazione diagnostica  
 Queste opzioni vengono offerte nel caso in cui Microsoft richieda di raccogliere informazioni avanzate per diagnosticare un problema. Le informazioni di registrazione non hanno utilità per gli utenti ed è consigliabile lasciarle disabilitate.  
  
 **Abilita registrazione**  
 Consente la registrazione diagnostica nella finestra di output.  
  
 **Livello di registrazione**  
 Impostare il livello di dettaglio da 0 a 5.  
  
 **Filtro di registrazione**  
 Filtra i tipi di eventi visualizzati usando una maschera di bit.  
  
 Impostare usando una somma di una qualsiasi delle opzioni seguenti:  
  
-   0 - Nessuno  
  
-   1 - Generale  
  
-   2 - Inattivo  
  
-   4 - Elemento di lavoro  
  
-   8 - IntelliSense  
  
-   16 - ACPerf  
  
-   32 - ClassView  
  
## <a name="fallback-location"></a>Percorso di fallback  
 Il percorso di fallback è la posizione in cui vengono inseriti il database di esplorazione del codice e i file di supporto IntelliSense (ad esempio, iPCH) quando il percorso principale (stessa directory della soluzione) non è in uso. Questa situazione può verificarsi quando l'utente non è in possesso delle autorizzazioni di scrittura per la directory della soluzione o se la directory della soluzione si trova in un dispositivo lento. Il percorso di fallback predefinito è nella directory temporanea dell'utente.  
  
 **Usa sempre percorso di fallback**  
 Indica che il database di esplorazione del codice e i file IntelliSense devono sempre essere archiviati in una cartella specificata come "Percorso di fallback" e non accanto al file con estensione sln. L'IDE non tenterà di inserire i file SDF o iPCH accanto alla directory della soluzione e verrà sempre usato il percorso di fallback.  
  
 **Non avvisare se viene utilizzato un percorso di fallback**  
 Non si viene informati e non viene suggerito l'uso di un 'Percorso di fallback'. In genere, sarà l'IDE a indicare se sia necessario usare il percorso di fallback. Questa opzione consente di disattivare l'avviso.  
  
 **Percorso di fallback**  
 Questo valore viene usato come un percorso secondario per archiviare il database di esplorazione del codice o i file IntelliSense. Per impostazione predefinita, la directory temporanea è il percorso di fallback. L'IDE creerà una sottodirectory nel percorso specificato (o nella directory temporanea) che include il nome della soluzione con un hash del percorso completo alla soluzione, che consente di evitare problemi in caso di nomi della soluzione identici.  
  
## <a name="intellisense"></a>IntelliSense  
 **Informazioni rapide automatiche**  
 Consente di visualizzare le descrizioni comandi delle informazioni rapide quando si passa il puntatore del mouse sul testo.  
  
 **Disabilita IntelliSense**  
 Disabilita tutte le funzionalità IntelliSense. L'IDE non crea processi VCPkgSrv.exe per soddisfare le richieste di IntelliSense e nessuna funzionalità IntelliSense funzionerà (InformazioniBase, Elenco membri, Completamento automatico, Guida Param). Sono anche disabilitate la colorazione semantica e l'evidenziazione dei riferimenti. Questa opzione non disabilita la funzionalità di esplorazione basata esclusivamente sul database (tra cui la barra di spostamento, ClassView e la finestra Proprietà).  
  
 **Disabilita aggiornamento automatico**  
 L'aggiornamento di IntelliSense verrà posticipato fino a una richiesta effettiva per IntelliSense. Questo ritardo può comportare un tempo di esecuzione più lungo della prima operazione di IntelliSense in un file, ma può essere utile impostare questa opzione sui computer molto lenti o con risorse limitate. Se si sceglie questa opzione, si scelgono anche in modo implicito le opzioni "Disabilita segnalazione errori" e "Disabilita controllo ortografia durante la digitazione".  
  
 **Disabilita segnalazione errori**  
 Disabilita la segnalazione errori di IntelliSense tramite il controllo ortografia durante la digitazione e la finestra Elenco errori. Disabilita anche l'analisi in background associata alla segnalazione errori. Se si sceglie questa opzione, si sceglie anche in modo implicito l'opzione "Disabilita controllo ortografia durante la digitazione".  
  
 **Disabilita controllo ortografia durante la digitazione**  
 Disabilita il controllo errori di ortografia durante la digitazione di IntelliSense. Le "righe rosse a zigzag" non vengono visualizzate nella finestra dell'editor, ma l'errore verrà comunque visualizzato nella finestra Elenco errori.  
  
 **Disabilita completamento automatico #include**  
 Disabilita il completamento automatico delle istruzioni `#include`.  
  
 **Usa barra in completamento automatico #include**  
 Attiva il completamento automatico delle istruzioni `#include` quando viene usato il carattere "/". Il delimitatore predefinito è una barra rovesciata '\'. Il compilatore può accettarle entrambe, pertanto usare questa opzione per specificare il carattere usato dalla base codice.  
  
 **Numero massimo di unità di conversione memorizzate nella cache**  
 Il numero massimo di unità di conversione che saranno mantenute attive alla volta per le richieste IntelliSense. Il valore deve essere compreso tra 2 e 15. Questo numero è direttamente correlato al numero massimo di processi VCPkgSrv.exe che verrà eseguito (per una determinata istanza di Visual Studio). Il valore predefinito è 2, ma in presenza di memoria disponibile è possibile aumentare questo valore e verosimilmente garantire prestazioni leggermente migliori in IntelliSense.  
  
 Per altre informazioni sulle unità di conversione, vedere [Phases of Translation](/cpp/preprocessor/phases-of-translation) (Fasi di conversione).  

 **Abilita sostituzione punto con freccia per elenco di membri**  
 sostituisce '.' con '->' quando applicabile per l'elenco membri.

 **Disabilita elenco di membri aggressivi**  
 L'elenco di membri non viene visualizzato quando si digita il nome di un tipo o variabile. L'elenco viene visualizzato solo dopo aver digitato uno dei caratteri di commit, come definito nell'opzione **Caratteri commit elenco membri**.  
  
 **Disabilita parole chiave elenchi di membri**  
 Le parole chiave del linguaggio, ad esempio `void`, `class`, `switch` non vengono visualizzate nei suggerimenti degli elenchi di membri.  
  
 **Disabilita frammenti di codice elenchi di membri**  
 I frammenti di codice non vengono visualizzati nei suggerimenti degli elenchi di membri.  
  
 **Disabilita colorazione semantica**  
 Disattiva tutte la colorazione del codice, ad eccezione di parole chiave del linguaggio, stringhe e commenti.  
  
 **Commit elenco membri smart**  
 Aggiunge una riga quando si sceglie INVIO alla fine di una parola digitata.  
  
 **Modalità filtro elenchi di membri**  
 Imposta il tipo di algoritmo di corrispondenza. **Fuzzy** consente di trovare le corrispondenze più probabili perché usa un algoritmo simile a un correttore ortografico per trovare corrispondenze simili ma non identiche. **Smart filtering** (Filtro intelligente) trova le corrispondenze nelle sottostringhe, anche se non sono all'inizio di una parola. **Prefisso** trova le corrispondenze solo in sottostringhe identiche all'inizio della parola.  
  
 **Caratteri commit elenco membri**  
 Specifica i caratteri che causano il commit del suggerimento elenco membri attualmente evidenziato. È possibile aggiungere o rimuovere caratteri da questo elenco.  
  
## <a name="references"></a>Riferimenti  
 **Disabilita risoluzione**  
 Per motivi prestazionali, 'Trova tutti i riferimenti' visualizza per impostazione predefinita i risultati della ricerca testuali non elaborati anziché usare IntelliSense per la verifica di ogni candidato. È possibile deselezionare questa casella di controllo per risultati più accurati su tutte le operazioni di ricerca. Per applicare un filtro basato sulla ricerca, aprire il menu di scelta rapida per l'elenco dei risultati e quindi scegliere "Risolvi risultati".  
  
 **Nascondi non confermati**  
 Nasconde gli elementi non confermati nei risultati 'Trova tutti i riferimenti'. Se non si imposta l'opzione "Disabilita risoluzione", questa opzione può essere usata per nascondere gli elementi non confermati nei risultati.  
  
 **Disabilita evidenziazione riferimento**  

 ## <a name="text-editor"></a>Editor di testo
 **Abilita espansione degli ambiti**  
 Se abilitata, è possibile racchiudere il testo selezionato tra parentesi graffe digitando '{' nell'editor di testo.  
  
 **Abilita espansione della precedenza**  
 Se abilitata, è possibile racchiudere il testo selezionato tra parentesi digitando '(' nell'editor di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione delle opzioni dell'editor specifiche del linguaggio](../../ide/reference/setting-language-specific-editor-options.md)
