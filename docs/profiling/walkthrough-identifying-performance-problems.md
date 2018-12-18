---
title: 'Procedura dettagliata: Identificazione dei problemi di prestazioni | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da961d153713c996c6f057e7bb0366c747c87205
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-identifying-performance-problems"></a>Procedura dettagliata: Identificazione dei problemi di prestazioni
Questa procedura dettagliata illustra come eseguire la profilatura di un'applicazione per identificare i problemi di prestazioni.  
  
 In questa procedura dettagliata verrà illustrato il processo di profilatura di un'applicazione gestita e sarà descritto come usare il campionamento e la strumentazione per isolare e identificare i problemi di prestazioni nell'applicazione.  
  
 In questa procedura dettagliata vengono illustrate le operazioni seguenti:  
  
-   Eseguire la profilatura di un'applicazione tramite il metodo di campionamento.  
  
-   Analizzare i risultati della profilatura campionati per individuare e risolvere un problema di prestazioni.  
  
-   Eseguire la profilatura di un'applicazione tramite il metodo di strumentazione.  
  
-   Analizzare i risultati della profilatura instrumentati per individuare e risolvere un problema di prestazioni.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   Conoscenza a livello intermedio di C#.  
  
-   Una copia dell'[esempio PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Per usare le informazioni fornite dalla profilatura, è consigliabile avere a disposizione informazioni sui simboli di debug.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilatura tramite il metodo di campionamento  
 Il campionamento è un metodo di profilatura mediante il quale viene eseguito periodicamente il polling del processo in questione per determinare la funzione attiva. I dati risultanti forniscono un conteggio della frequenza con cui la funzione si trovava all'inizio dello stack di chiamate quando è stato eseguito il campionamento del processo.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Per eseguire la profilatura di un'applicazione tramite il metodo di campionamento  
  
1.  Aprire [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] con privilegi di amministratore. Per eseguire la profilatura, è necessario essere un amministratore.  
  
2.  Aprire la soluzione PeopleTrax.  
  
     La soluzione PeopleTrax verrà inserita in Esplora soluzioni.  
  
3.  Impostare l'opzione di configurazione del progetto su **Rilascio**.  
  
     Usare una build di rilascio per rilevare i problemi di prestazioni nell'applicazione. Per la profilatura è consigliata una build di rilascio perché una build di debug contiene informazioni aggiuntive che potrebbero influire negativamente sulle prestazioni e non indicare in modo accurato i problemi di prestazioni.  
  
4.  Dal menu **Analizza** scegliere **Profiler prestazioni**, **Creazione guidata sessione di prestazioni** e quindi selezionare **Avvia**.  
  
     Verrà visualizzata la Creazione guidata sessione di prestazioni.  
  
5.  Verificare che sia selezionato **Campionamento CPU (consigliato)** e quindi fare clic su **Avanti**.  
  
6.  In **Specificare l'applicazione di destinazione per la profilatura** selezionare PeopleTrax e quindi fare clic su **Avanti**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] compila il progetto e avvia la profilatura dell'applicazione. Verrà visualizzata la finestra dell'applicazione **PeopleTrax**.  
  
7.  Fare clic su **Get People**.  
  
8.  Fare clic su **ExportData**.  
  
     Verrà aperto il Blocco note con un nuovo file che contiene i dati esportati da **PeopleTrax**.  
  
9. Chiudere il Blocco note e quindi chiudere l'applicazione **PeopleTrax**.  
  
     Il profiler genera un file di dati di profilatura (\*.vsp), elenca il nome del file nella sezione Report della finestra Esplora prestazioni e carica automaticamente la visualizzazione **Riepilogo** del file di dati nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Per analizzare i risultati della profilatura campionati  
  
1.  La visualizzazione Riepilogo mostra una sequenza temporale dell'utilizzo della CPU nel corso dell'esecuzione della profilatura, l'elenco **Percorso critico** che rappresenta il ramo più attivo dell'albero delle chiamate dell'applicazione e un elenco **Funzioni che svolgono più lavoro individuale** che mostra le funzioni che sono state campionate più di frequente durante l'esecuzione del codice nel corpo della funzione.  
  
     Esaminando l'elenco **Percorso critico**, è possibile osservare che il metodo PeopleNS.People.GetNames è la funzione PeopleTrax più vicina alla fine dell'elenco. La sua posizione la rende un buon candidato per l'analisi. Fare clic sul nome della funzione per visualizzare i dettagli di GetNames nella visualizzazione **Dettagli funzione**.  
  
2.  La visualizzazione **Dettagli funzione** contiene due finestre. La finestra di distribuzione dei costi fornisce una visualizzazione grafica del lavoro svolto dalla funzione, del lavoro svolto dalle funzioni che questa ha chiamato e del contributo delle funzioni che hanno chiamato la funzione per il numero di istanze campionate. È possibile modificare la funzione rappresentata della visualizzazione facendo clic sul nome di una funzione. È ad esempio possibile fare clic su PeopleNS.People.GetPeople per rendere GetPeople la funzione selezionata.  
  
     La finestra **Visualizzazione codice funzione** mostra il codice sorgente per la funzione, se disponibile, ed evidenzia le righe più costose della funzione selezionata. Quando si seleziona GetNames, è possibile notare che questa funzione legge una stringa dalle risorse dell'applicazione e quindi usa una classe <xref:System.IO.StringReader> per aggiungere ogni riga nella stringa a una classe <xref:System.Collections.ArrayList>. Non esiste un modo ovvio per ottimizzare questa funzione.  
  
3.  Poiché PeopleNS.People.GetPeople è il solo chiamante di GetNames, fare clic su GetPeople nella finestra di distribuzione dei costi per esaminarne il codice. Questo metodo restituisce una classe <xref:System.Collections.ArrayList> di oggetti PersonInformationNS.PersonInformation dai nomi di persone e di aziende prodotti da GetNames. Tuttavia, GetNames viene chiamata due volte ogni volta che viene creato un oggetto PersonInformation. È possibile vedere che il metodo può essere facilmente ottimizzato creando gli elenchi una sola volta all'inizio del metodo e indicizzando tali elenchi durante il ciclo di creazione di PersonInformation.  
  
4.  Una versione alternativa di GetPeople viene fornita con il codice dell'applicazione di esempio ed è possibile chiamare la funzione ottimizzata aggiungendo un simbolo di compilazione condizionale alle proprietà di compilazione. Nella finestra Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto People e scegliere **Proprietà**. Fare clic su **Genera** nel menu della pagina delle proprietà e quindi digitare **OPTIMIZED_GETPEOPLE** nella casella di testo per il simbolo di compilazione condizionale. La versione ottimizzata di GetPeople sostituisce il metodo originale nella compilazione successiva.  
  
5.  Eseguire nuovamente la sessione di prestazioni. Nella barra degli strumenti di Esplora prestazioni fare clic su **Avvio con analisi**. Fare clic su **Get People** e quindi su **Esporta dati**. Chiudere la finestra del Blocco note visualizzata e quindi chiudere l'applicazione PeopleTrax.  
  
     Verrà generato un nuovo file di dati di profilatura e sarà mostrata una visualizzazione **Riepilogo** per i nuovi dati nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  Per confrontare le due esecuzioni della profilatura, selezionare i due file di dati in Esplora prestazioni, fare clic con il pulsante destro del mouse sui file e quindi scegliere **Confronta rapporto di prestazioni**. Viene visualizzata una finestra Rapporto di confronto nella finestra principale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. La colonna **Delta** mostra la modifica del valore delle prestazioni delle funzioni, dal valore precedente **Linea di base** al valore successivo **Confronto**. È possibile selezionare i valori da confrontare nell'elenco a discesa **Colonna**. Selezionare **% esempi inclusivi**.  
  
     Si noti che i metodi GetPeople e GetNames mostrano notevoli miglioramenti delle prestazioni.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilatura tramite il metodo di strumentazione  
 La strumentazione è un metodo di profilatura in cui il profiler inserisce funzioni probe in particolari versioni dei file binari profilati. I probe raccolgono informazioni sugli intervalli all'ingresso e all'uscita delle funzioni nei moduli instrumentati e in tutto il sito di chiamata in tali funzioni. Il processo di strumentazione è utile per l'analisi dei problemi relativi alle operazioni di input/output, come la scrittura su disco e le comunicazioni di rete. La strumentazione fornisce informazioni più dettagliate del campionamento, ma è più intrusiva nell'esecuzione del processo e comporta una maggiore quantità di overhead. I file binari instrumentati sono anche più grandi dei file binari di debug o di rilascio e non sono destinati alla distribuzione.  
  
 In questa sezione della procedura dettagliata verrà usato il metodo di strumentazione per individuare altro codice che è possibile ottimizzare nell'applicazione PeopleTrax di cui è stata precedentemente eseguita la profilatura. Usando il filtro della sequenza temporale della visualizzazione Riepilogo, verrà analizzato lo scenario di esportazione dei dati nell'applicazione profilata, in cui l'elenco di persone viene scritto in un file di Blocco note.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Per eseguire la profilatura di un'applicazione esistente tramite il metodo di strumentazione  
  
1.  Se necessario, aprire l'applicazione PeopleTrax in Visual Studio.  
  
     Assicurarsi di usare un account di amministratore e verificare che la configurazione della build per la soluzione sia impostata su **Rilascio**.  
  
2.  In Esplora prestazioni fare clic su **Strumentazione**.  
  
3.  Nella barra degli strumenti di Esplora prestazioni fare clic su **Avvio con analisi**.  
  
     Il profiler compila il progetto e avvia la profilatura dell'applicazione. Verrà visualizzata la finestra dell'applicazione PeopleTrax.  
  
4.  Fare clic su **Get People**.  
  
     Verranno inseriti dati nella griglia dei dati di PeopleTrax.  
  
5.  Attendere circa 10 secondi e quindi fare clic su **Esporta dati**.  
  
     Verrà avviato il **Blocco note** e sarà visualizzato un nuovo file che contiene un elenco di persone di PeopleTrax. L'attesa consente di identificare più facilmente la procedura di esportazione dei dati per il filtro.  
  
6.  Chiudere il **Blocco note** e quindi chiudere l'applicazione **PeopleTrax**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] genera un report della sessione di prestazioni (con estensione vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Per analizzare i risultati della profilatura instrumentati  
  
1.  Il grafico della sequenza temporale della visualizzazione **Riepilogo** del report mostra l'utilizzo della CPU del programma per la durata dell'esecuzione della profilatura. L'operazione di esportazione dei dati dovrebbe essere il picco o il livello elevato sul lato destro del grafico. È possibile filtrare la sessione di prestazioni per visualizzare e analizzare solo i dati raccolti durante l'operazione di esportazione. Fare clic a sinistra del punto nel grafico in cui inizia l'operazione di esportazione dei dati. Fare nuovamente clic sul lato destro dell'operazione. Fare quindi clic su **Filtro in base a selezione** nell'elenco di collegamenti a destra della sequenza temporale.  
  
     L'albero **Percorso critico** illustra che il metodo <xref:System.String.Concat%2A> chiamato dal metodo PeopleTrax.Form1.ExportData usa una percentuale elevata di tempo. Poiché anche **System.String.Concat** è all'inizio dell'elenco **Funzioni con più lavoro individuale**, la riduzione del tempo impiegato nella funzione è un probabile punto di ottimizzazione.  
  
2.  Fare doppio clic su **System.String.Concat** in una delle tabelle di riepilogo per visualizzare altre informazioni nella visualizzazione Dettagli funzione.  
  
3.  È possibile osservare che PeopleTrax.Form1.ExportData è l'unico metodo che chiama Concat. Fare clic su **PeopleTrax.Form1.ExportData** nell'elenco **Funzioni chiamanti** per selezionare il metodo come destinazione della visualizzazione Dettagli funzione.  
  
4.  Esaminare il metodo nella finestra Visualizzazione codice funzione. Si noti che non sono presenti chiamate letterali a **System.String.Concat**. Sono invece presenti diversi usi dell'operando +=, che il compilatore sostituisce con chiamate a **System.String.Concat**. Qualsiasi modifica a una stringa in .NET Framework causa l'allocazione di una nuova stringa. .NET Framework include una classe <xref:System.Text.StringBuilder> ottimizzata per la concatenazione delle stringhe  
  
5.  Per sostituire quest'area problematica con codice ottimizzato, aggiungere OPTIMIZED_EXPORTDATA come simbolo di compilazione condizionale al progetto PeopleTrax.  
  
6.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto PeopleTrax e scegliere **Proprietà**.  
  
     Viene visualizzato il form delle proprietà del progetto PeopleTrax.  
  
7.  Fare clic sulla scheda **Generazione**.  
  
8.  Nella casella di testo **Simboli di compilazione condizionale** digitare **OPTIMIZED_EXPORTDATA**.  
  
9. Chiudere il form delle proprietà del progetto e scegliere **Salva tutto** quando richiesto.  
  
 Quando si esegue nuovamente l'applicazione, sarà possibile osservare notevoli miglioramenti delle prestazioni. È consigliabile ripetere la sessione di profilatura, anche se si registrano miglioramenti delle prestazioni visibili all'utente. Esaminare i dati dopo aver risolto un problema è importante perché il primo problema potrebbe nascondere altri problemi.  
  
## <a name="see-also"></a>Vedere anche  
 [Overviews](../profiling/overviews-performance-tools.md)  (Panoramiche)  
 [Introduzione](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format)