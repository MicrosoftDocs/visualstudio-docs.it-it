---
title: Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPag.Environment.Fonts_And_Colors
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 23e6712dbf66c898757176aca9e89b98de2f65bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni
La pagina **Tipi di carattere e colori** della finestra di dialogo **Opzioni** consente di definire una combinazione di colori e tipi di carattere personalizzata per vari elementi dell'interfaccia utente nell'ambiente di sviluppo integrato (IDE). Per accedere a questa finestra di dialogo, fare clic su **Strumenti/Opzioni** e quindi selezionare **Ambiente/Tipi di carattere e colori**. Se questa pagina non viene visualizzata nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 Le modifiche delle combinazioni colori non diventano effettive durante la sessione in cui vengono eseguite. È possibile valutare le modifiche ai colori aprendo un'altra istanza di Visual Studio e riproducendo le condizioni in cui si prevede vengano applicate le modifiche apportate.  
  
 **Mostra impostazioni per**  
 Elenca tutti gli elementi dell'interfaccia utente per cui è possibile modificare le combinazioni di tipi i carattere e colori. Dopo aver selezionato un elemento in questo elenco è possibile personalizzare le impostazioni dei colori per l'elemento selezionato in **Elementi visualizzati**.  
  
-   **Editor di testo**  
  
     Le modifiche apportate alle impostazioni di visualizzazione per stile, dimensione e colore dei caratteri per l'Editor di testo influiscono sull'aspetto del testo nell'editor di testo predefinito. I documenti aperti in un editor di testo all'esterno dell'IDE non saranno interessati da queste impostazioni.  
  
-   **Stampante**  
  
     Le modifiche apportate alle impostazioni di visualizzazione per stile, dimensione e colore dei caratteri per gli elementi Stampante influiscono sull'aspetto del testo nei documenti stampati.  
  
    > [!NOTE]
    >  Se necessario, è possibile selezionare un tipo di carattere predefinito per la stampa diverso da quello usato per la visualizzazione nell'editor di testo. Questo può essere utile durante la stampa di codice che contiene sia caratteri a un byte che DBCS.  
  
-   **Completamento istruzioni**  
  
     Modifica lo stile e la dimensione del carattere per il testo visualizzato nel popup di completamento delle istruzioni nell'editor.  
  
-   **Descrizione comando editor**  
  
     Modifica lo stile e la dimensione del carattere per il testo visualizzato nelle descrizioni comandi visualizzate nell'editor.  
  
-   **Tipo di carattere ambiente**  
  
     Modifica lo stile e la dimensione del carattere per tutti gli elementi dell'interfaccia utente dell'IDE per i quali non è stata ancora impostata un'opzione separata in **Mostra impostazioni per**. Questa opzione è valida, ad esempio, per la **Pagina iniziale** ma non influisce sulla finestra di **Output**.  
  
-   **[Tutte le finestre degli strumenti di testo]**  
  
     Le modifiche apportate alle impostazioni di visualizzazione per stile, dimensione e colore dei caratteri per questo elemento influiscono sull'aspetto del testo nelle finestre degli strumenti con riquadri di output nell'IDE. Ad esempio, finestra di output, finestra di comando, finestra di controllo immediato e così via.  
  
    > [!NOTE]
    >  Le modifiche al testo degli elementi **[Tutte le finestre degli strumenti di testo]** non sono effettive durante la sessione in cui vengono eseguite. È possibile valutare le modifiche apportate aprendo un'altra istanza di Visual Studio.  
  
**Valori predefiniti**  
Reimposta i valori relativi al tipo di carattere e al colore dell'elemento elenco selezionato in **Mostra impostazioni per**. Il pulsante **Usa** viene visualizzato quando sono disponibili per la selezione altre combinazioni di visualizzazione. Ad esempio, è possibile scegliere tra due combinazioni per l'elemento Stampante.  
  
**Carattere (tipi di carattere a larghezza fissa in grassetto)**  
Elenca tutti i tipi di carattere installati nel sistema. La prima volta che viene visualizzato il menu a discesa, nel campo **Mostra impostazioni per** viene evidenziato il tipo di carattere corrente per l'elemento selezionato. I tipi di carattere a larghezza fissa, più facili da allineare nell'editor, sono visualizzati in grassetto.  
  
**Dimensione**  
Elenca le dimensioni in punti disponibili per il tipo di carattere evidenziato. La modifica della dimensione del carattere influisce su tutti gli **Elementi visualizzati** disponibili per la selezione in **Mostra impostazioni per**.  
  
**Elementi visualizzati**  
Elenca gli elementi per cui è possibile modificare il colore di primo piano e sfondo.  
  
> [!NOTE]
>  L'elemento visualizzato predefinito è **Testo normale**. Di conseguenza, le proprietà assegnate a **Testo normale** verranno sostituite dalle proprietà assegnate ad altri elementi visualizzati. Se, ad esempio, si assegna il colore blu a **Testo normale** e il colore verde a **Identificatore**, tutti gli identificatori verranno visualizzati in verde. In questo esempio le proprietà di **Identificatore** sostituiscono le proprietà di **Testo normale**.  
  
 Alcuni degli elementi visualizzati includono:  
  
|Elemento visualizzato|Descrizione|  
|------------------|-----------------|  
|**Testo normale**|Testo nell'editor.|  
|**Testo selezionato**|Testo incluso nella selezione corrente quando l'editor ha lo stato attivo.|  
|**Testo selezionato inattivo**|Testo incluso nella selezione corrente quando l'editor perde lo stato attivo.|  
|**Margine indicatore**|Il margine a sinistra dell'Editor di codice in cui vengono visualizzate le icone dei punti di interruzione e dei segnalibri.|  
|**Numeri di riga**|Numeri facoltativi visualizzati accanto a ogni riga di codice|  
|**Spazio vuoto visibile**|Spazi, tabulazioni e indicatori di a capo automatico|  
|**Segnalibro**|Righe con segnalibri. L'opzione **Segnalibro** è visibile solo se viene disabilitato il margine indicatore.|  
|**Corrispondenza parentesi graffe (evidenziate)**|Evidenziazione per cui viene in genere usato il formato grassetto per le parentesi graffe corrispondenti.|  
|**Corrispondenza parentesi graffe (rettangolo)**|Evidenziazione per cui viene in genere usato un rettangolo grigio nello sfondo.|  
|**Punto di interruzione (disabilitato)**|Non usato.|  
|**Punto di interruzione (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione semplici. Questa opzione è applicabile solo se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione in stato di errore. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione in stato di avviso. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione - Avanzato (disabilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione condizionali o con numero di passaggi disabilitati. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione - Avanzato (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione condizionali o con numero di passaggi. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione - Avanzato (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione condizionali o con numero di passaggi in stato di errore. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione - Avanzato (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione condizionali o con numero di passaggi in stato di avviso. Applicabile solo se sono attivi i punti di interruzione a livello di istruzione o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md) è selezionata.|  
|**Punto di interruzione - Mappato (disabilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione mappati disabilitati. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di interruzione - Mappato (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione mappati. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di interruzione - Mappato (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione mappati in stato di errore. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di interruzione - Mappato (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di interruzione mappati in stato di avviso. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Parole chiave utente C/C++**|Costante all'interno di un file di codice specifico definita tramite la direttiva `#define`.|  
|**Risultato della chiamata**|Specifica il colore di evidenziazione per le istruzioni o le righe di origine che indicano i punti di risultato della chiamata quando il contesto passa a uno stack frame non all'inizio dello stack durante il debug.|  
|**Campo dipendente da frammento di codice**|Un campo che verrà aggiornato in seguito alla modifica del campo modificabile corrente.|  
|**Campo frammento di codice**|Campo modificabile quando è attivo un frammento di codice.|  
|**Testo comprimibile**|Un blocco di testo o codice che può essere aggiunto o rimosso dalla visualizzazione all'interno dell'Editor di codice.|  
|**Commentoo**|Commenti del codice.|  
|**Errore del compilatore**|Linee a zigzag blu nell'editor che indicano un errore del compilatore.|  
|**Area non interessata dal code coverage**|Codice non interessato da un unit test.|  
|**Area parzialmente interessata dal code coverage**|Codice interessato parzialmente da un unit test.|  
|**Area interessata dal code coverage**|Codice interessato totalmente da un unit test.|  
|**Commento CSS**|Commento in CSS (Cascading Style Sheets). Ad esempio:<br /><br /> /* commento \*/|  
|**Parola chiave CSS**|Parole chiave nel foglio di stile CSS.|  
|**Nome proprietà CSS**|Nome di una proprietà, ad esempio Background.|  
|**Valore proprietà CSS**|Valore assegnato a una proprietà, ad esempio blue.|  
|**Selettore CSS**|Stringa che identifica gli elementi a cui viene applicata la regola corrispondente. Un selettore può essere un selettore semplice, come 'H1' o contestuale, ad esempio 'H1 B', costituito da più selettori semplici.|  
|**Valore stringa CSS**|Una stringa in CSS (Cascading Style Sheets).|  
|**Percorso elenco corrente**|Riga corrente a cui si è passati in una finestra dello strumento di elenco, ad esempio la finestra di output o le finestre Risultati ricerca.|  
|**Istruzione corrente**|Specifica il colore di evidenziazione per l'istruzione o la riga di origine che indica la posizione del passaggio corrente durante il debug.|  
|**Dati debugger modificati**|Colore del testo usato per visualizzare i dati modificati all'interno delle finestre **Registri** e **Memoria**.|  
|**Sfondo della finestra Definizione**|Colore di sfondo della finestra **Definizione codice**.|  
|**Corrispondenza corrente della finestra Definizione**|Definizione corrente nella finestra **Definizione codice**.|  
|**Nome file disassembly**|Colore del testo usato per visualizzare le interruzioni di nomi di file all'interno della finestra **Disassembly**.|  
|**Origine disassembly**|Colore del testo usato per visualizzare le righe di origine all'interno della finestra **Disassembly**.|  
|**Simbolo disassembly**|Colore del testo usato per visualizzare i nomi di simboli all'interno della finestra **Disassembly**.|  
|**Testo disassembly**|Colore del testo usato per visualizzare il codice operativo e i dati all'interno della finestra **Disassembly**.|  
|**Codice escluso**|Codice che non deve essere compilato in base a una direttiva per il preprocessore condizionale come `#if`.|  
|**Identificatore**|Identificatori nel codice, ad esempio i nomi di classi, metodi e variabili.|  
|**Parola chiave**|Parole chiave riservate per il linguaggio specificato. Ad esempio: class e namespace.|  
|**Indirizzo di memoria**|Colore del testo usato per visualizzare la colonna dell'indirizzo all'interno della finestra **Memoria**.|  
|**Memoria modificata**|Colore del testo usato per visualizzare i dati modificati all'interno della finestra **Memoria**.|  
|**Dati memoria**|Colore del testo usato per visualizzare i dati all'interno della finestra **Memoria**.|  
|**Memoria illeggibile**|Colore del testo usato per visualizzare le aree della memoria illeggibili all'interno della finestra **Memoria**.|  
|**Numero**|Numero nel codice che rappresenta un valore numerico effettivo.|  
|**Operator**|Operatori come +, - e !=.|  
|**Altro errore**|Altri tipi di errore non coperti da altre sottolineature a zigzag per gli errori. Attualmente sono incluse le modifiche non applicabili in Modifica e continuazione.|  
|**Parola chiave preprocessore**|Parole chiave usate dal preprocessore come #include.|  
|**Area in sola lettura**|Codice non modificabile. Ad esempio codice visualizzato nella finestra Definizione codice o codice che non può essere modificato durante Modifica e continuazione.|  
|**Effettua refactoring dello sfondo**|Colore di sfondo della finestra di dialogo **Anteprima modifiche**.|  
|**Effettua refactoring del campo corrente**|Colore di sfondo dell'elemento corrente di cui effettuare il refactoring nella finestra di dialogo **Anteprima modifiche**.|  
|**Effettua refactoring del campo dipendente**|Colore o riferimenti dell'elemento di cui effettuare il refactoring nella finestra di dialogo **Anteprima modifiche**.|  
|**Registra dati**|Colore del testo usato per visualizzare i dati all'interno della finestra **Registri**.|  
|**Registra NAT**|Colore del testo usato per visualizzare i dati e gli oggetti non riconosciuti all'interno della finestra **Registri**.|  
|**Smart tag**|Usato per indicare la struttura quando vengono richiamati gli smart tag.|  
|**Indicatore DML SQL**|Si applica all'editor Transact-SQL. Per impostazione predefinita, le istruzioni DML in questo editor sono contrassegnate con un rettangolo blu.|  
|**Codice non aggiornato**|Codice obsoleto in attesa di aggiornamento. In alcuni casi la funzionalità Modifica e continuazione non consente di applicare immediatamente modifiche al codice, ma le applicherà in seguito mentre si continua con il debug. Ciò si verifica quando si modifica una funzione che deve chiamare la funzione in esecuzione o si aggiungono più di 64 byte di nuove variabili a una funzione in attesa nello stack di chiamate. In questo caso, il debugger viene visualizzata una finestra di dialogo "Avviso di codice non aggiornato" e il codice obsoleto continua a essere eseguito fino a quando la funzione in questione non termina e viene chiamata nuovamente. Questo è il momento in cui Modifica e continuazione applica le modifiche.|  
|**String**|Valori letterali stringa.|  
|**Stringa (C# @ Verbatim)**|Valori letterali stringa in C# che vengono interpretati come verbatim. Ad esempio:<br /><br /> @"x"|  
|**Errore di sintassi**|Errori di analisi.|  
|**Collegamento Elenco attività**|Se a una riga viene aggiunto un collegamento **Elenco attività** e il margine indicatore è disabilitato, la riga verrà evidenziata.|  
|**Punto di analisi (disabilitato)**|Non usato.|  
|**Punto di analisi (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi semplici. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi in stato di errore. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi in stato di avviso. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Avanzato (disabilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi condizionali o con numero di passaggi disabilitati. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Avanzato (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi condizionali o con numero di passaggi. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Avanzato (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi condizionali o con numero di passaggi in stato di errore. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Avanzato (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi condizionali o con numero di passaggi in stato di avviso. Questa opzione è applicabile solo se i punti di analisi a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Mappato (disabilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi mappati disabilitati. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Mappato (abilitato)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi mappati. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Mappato (errore)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi mappati in stato di errore. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punto di analisi - Mappato (avviso)**|Specifica il colore di evidenziazione per le istruzioni o le righe contenenti punti di analisi mappati in stato di avviso. Applicabile per il debug ASP o ASP.NET se i punti di interruzione a livello di istruzione sono attivi o se l'opzione **Evidenzia intera riga di origine per i punti di interruzione e l'istruzione corrente** è selezionata in [Generale, Debug, finestra di dialogo Opzioni](../../debugger/general-debugging-options-dialog-box.md).|  
|**Revisioni dopo il salvataggio**|Righe di codice che sono state modificate dopo l'apertura del file ma sono salvate su disco.|  
|**Revisioni prima del salvataggio**|Righe di codice che sono state modificate dopo l'apertura del file ma non sono salvate su disco.|  
|**Tipi utente**|Tipi definiti dagli utenti.|  
|**Tipi utente (delegati)**|Colore del tipo per i delegati.|  
|**Tipi utente (enum)**|Colore del tipo usato per le enumerazioni.|  
|**Tipi utente (interfacce)**|Colore del tipo per le interfacce.|  
|**Tipi utente (tipi di valore)**|Colore del tipo per i tipi valore come struct in C#.|  
|**Indicatore di sola lettura di Visual Basic**|Indicatore specifico di Visual Basic usato per designare EnC, ad esempio aree di eccezione, una definizione di metodo e frame di chiamata non foglia.|  
|**Avviso**|Avvisi del compilatore.|  
|**Percorso righe di avviso**|Usato per le righe di avviso di analisi statica.|  
|**Attributo XML**|Nomi di attributi.|  
|**Virgolette per l'attributo XML**|Virgolette per gli attributi XML.|  
|**Valore dell'attributo XML**|Contenuto degli attributi XML.|  
|**Sezione CData XML**|Contenuto di \<![CDATA[...]]>.|  
|**Commento XML**|Contenuto di \<!-- -->.|  
|**Delimitatore XML**|Delimitatori di sintassi XML, tra cui <, <?, <!, \<!--, -->, ?\>, \<![, ]]> e [, ].|  
|**Attributo documento XML**|Valore di un attributo di documentazione XML, come \<param name="I"> dove la "I" è colorata.|  
|**Commento documento XML**|Commenti racchiusi nei commenti della documentazione XML.|  
|**Tag documento XML**|Tag nei commenti della documentazione XML, ad esempio<br /><br /> /// \<summary>.|  
|**Parola chiave XML**|Parole chiave DTD quali CDATA, IDREF e NDATA.|  
|**Nome XML**|Nome di destinazione di elementi e istruzioni di elaborazione.|  
|**Istruzioni di elaborazione XML**|Contenuto delle istruzioni di elaborazione, escluso il nome di destinazione.|  
|**Testo XML**|Contenuto dell'elemento in testo normale.|  
|**Parola chiave XSLT**|Nomi di elementi XSLT.|  
  
 **Primo piano elemento**  
 Elenca i colori disponibili che è possibile scegliere per il primo piano dell'elemento selezionato in **Elementi visualizzati**. Poiché alcuni elementi sono correlati ed è preferibile che abbiano uno schema di visualizzazione coerente, la modifica del colore del testo di primo piano modifica anche i valori predefiniti per elementi quali Errore del compilatore, Parola chiave o Operatore.  
  
 **Automatico** Gli elementi possono ereditare il colore di primo piano da altri elementi visualizzati come **Testo normale**. Con questa opzione, quando si modifica il colore di un elemento visualizzato ereditato, cambia automaticamente anche il colore degli elementi visualizzati correlati. Ad esempio, se si seleziona il valore **Automatico** per **Errore del compilatore** e in seguito si modifica il colore di **Testo normale** impostando il rosso, il colore rosso viene ereditato automaticamente anche da **Errore del compilatore**.  
  
 **Predefinito** Il colore visualizzato per l'elemento la prima volta che si avvia Visual Studio. È possibile fare clic sul pulsante **Valori predefiniti** per reimpostare questo colore.  
  
 **Personalizzato**  
 Visualizza la finestra di dialogo Colore che consente di impostare un colore personalizzato per l'elemento selezionato nell'elenco Elementi visualizzati.  
  
> [!NOTE]
>  La possibilità di definire colori personalizzati può essere limitata dalle impostazioni del colore per lo schermo del computer. Ad esempio, se il computer è impostato su 256 colori e si seleziona un colore personalizzato nella finestra di dialogo **Colore**, l'IDE userà per impostazione predefinita il **colore di base** più simile disponibile e visualizzerà il colore nero nella casella di anteprima **Colore**.  
  
 **Sfondo elemento**  
 Visualizza una tavolozza di colori da cui è possibile scegliere un colore di sfondo per l'elemento selezionato in **Elementi visualizzati**. Poiché alcuni elementi sono correlati ed è preferibile che abbiano uno schema di visualizzazione coerente, la modifica del colore del testo di sfondo modifica anche i valori predefiniti per elementi quali Errore del compilatore, Parola chiave o Operatore.  
  
 **Automatico** Gli elementi possono ereditare il colore di sfondo da altri elementi visualizzati come **Testo normale**. Con questa opzione, quando si modifica il colore di un elemento visualizzato ereditato, cambia automaticamente anche il colore degli elementi visualizzati correlati. Ad esempio, se si seleziona il valore **Automatico** per **Errore del compilatore** e in seguito si modifica il colore di **Testo normale** impostando il rosso, il colore rosso viene ereditato automaticamente anche da **Errore del compilatore**.  
  
 **Predefinito** Il colore visualizzato per l'elemento la prima volta che si avvia Visual Studio. È possibile fare clic sul pulsante **Valori predefiniti** per reimpostare questo colore.  
  
 **Personalizzato**  
 Visualizza la finestra di dialogo Colore che consente di impostare un colore personalizzato per l'elemento selezionato nell'elenco Elementi visualizzati.  
  
 **Grassetto**  
 Selezionare questa opzione per visualizzare in grassetto il testo dell'elemento selezionato in **Elementi visualizzati**. Il testo in grassetto è più facile da individuare nell'editor.  
  
 **Esempio**  
 Visualizza un esempio dello stile, della dimensione e della combinazione colori del carattere per le opzioni selezionate in **Mostra impostazioni per** ed **Elementi visualizzati**. È possibile usare questa casella per visualizzare in anteprima i risultati mentre si sperimentano diverse opzioni di formattazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Environment Options Dialog Box](../../ide/reference/environment-options-dialog-box.md)  (Ambiente, finestra di dialogo Opzioni)  
 [Finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md)   
 [Procedura: Modificare i tipi di carattere e colori](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)