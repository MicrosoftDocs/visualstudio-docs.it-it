---
title: Debug di progetti Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c3a3b4d3eebd5b20c4e9eb56b30a8980ceafb8bf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="debugging-office-projects"></a>Debug di progetti di Office
  È possibile eseguire il debug di progetti di Office usando gli stessi strumenti di Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che si usano per altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Le funzionalità del debugger di[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ad esempio la possibilità di inserire punti di interruzione e visualizzare le variabili nella finestra **Variabili locali** , sono disponibili anche quando si esegue il debug di progetti di Office. Per altre informazioni sugli strumenti di debug [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , vedere [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Per semplificare il debug, chiudere tutte le istanze dell'applicazione di Office aperte, prima di generare ed eseguire il debug.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="starting-and-stopping-the-debugger"></a>Avvio e arresto del debug  
 È possibile avviare il debug di un progetto di Office come si avvia il debug di altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ad esempio è possibile premere il tasto F5. Quando si avvia il debug di un progetto di componente aggiuntivo VSTO, viene avviato un nuovo processo per l'applicazione di Office di destinazione e il componente aggiuntivo VSTO viene caricato.  
  
 Quando si avvia il debug di un progetto a livello di documento, il documento o la cartella di lavoro viene aperta in un nuovo processo di Word o Excel.  
  
 Quando si arresta il debugger, il debugger interrompe improvvisamente il processo di applicazione o viene disconnesso se il debugger è impostato per disconnettersi. Tutti gli altri documenti aperti nel processo dell'applicazione di Office terminata vengono chiusi senza avviso e le modifiche non salvate vengono perse. Questo potrebbe includere tutti i documenti o le cartelle di lavoro che vengono aperti durante l'esecuzione del debugger.  
  
 In genere, si consiglia di disconnettersi dal processo prima di arrestare il debugger in modo da poter chiudere l'applicazione di Office in modo normale. È anche possibile disconnettersi dal processo per prima cosa se si desidera usare un documento o un foglio di lavoro aperto dopo l'arresto del debugger.  
  
 Se si esegue il debug di una personalizzazione a livello di documento per Word, arrestando ripetutamente il debugger e causando la chiusura improvvisa di Word, si può danneggiare il modello Normale. In questo caso, è possibile eliminare il modello Normale danneggiato che verrà ricreato automaticamente alla successiva apertura di Word. Tuttavia, non vengono ricreate le macro che sono state archiviate nel modello Normale.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Eseguire il debug dei componenti aggiuntivi VSTO di Office 2013 con Office 2013 o Office 2016  
 Se si utilizza Visual Studio 2015 e si dispone di entrambe le versioni di Office installate side-by-side, Visual Studio avvia Office 2016. Se si utilizza Visual Studio 2013, Visual Studio avvia Office 2013.  
  
 Per eseguire il debug del componente aggiuntivo VSTO con una versione di Office diversa (2013 o 2016), aprire **Creazione progetti**e scegliere il pulsante di opzione **Avvia programma esterno** nella scheda **Debug** . Quindi, passare al percorso dell'eseguibile dell'applicazione di Office appropriata.  
  
## <a name="f10-and-f11-behavior"></a>Comportamento di F10 e F11  
 Quando si avvia il debug di un progetto di Office, F10 e F11 non hanno lo stesso comportamento di quando si avvia il debug di altri progetti di Visual Basic o C#. Nei progetti Visual Basic o C#, il debugger si arresta sulla funzione principale. Nei progetti di Office, Visual Studio non dispone di controllo sulla funzione principale dell'applicazione di Office. Tuttavia, durante il debug, F10 e F11 hanno le stesse funzioni come per i progetti di Visual Basic e C#.  
  
## <a name="displaying-exceptions"></a>Visualizzazione delle eccezioni  
 A causa del modo con cui il codice gestito interagisce con il codice non gestito, in Visual Studio non vengono visualizzati gli errori generati dalle applicazioni di Microsoft Office. Ad esempio, se un componente aggiuntivo VSTO creato con gli strumenti di sviluppo di Office in Visual Studio genera un'eccezione, l'applicazione di Microsoft Office continua senza visualizzare alcun errore. Per visualizzare questi errori, impostare il debugger in modo che si interrompa in caso di eccezioni di Common Language Runtime. Per ulteriori informazioni, vedere [la gestione delle eccezioni con il debugger](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Se si imposta il debugger per interrompere l'esecuzione in caso di eccezioni di Common Language Runtime, tutte le eccezioni a questo punto verranno interrotte nel debugger, incluse quelle gestite e alcune eccezioni first-chance del runtime stesso che potrebbero non essere rilevanti per il progetto. Gli errori che fanno riferimento a msosec non trovato, vengono visualizzati in ogni progetto, ma è possibile ignorarli. Queste eccezioni msosec non avranno effetto sulla soluzione.  
  
 È inoltre possibile usare le istruzioni **Try...Catch** sui metodi per raccogliere le eccezioni.  
  
 Per impostazione predefinita, in Visual Studio non vengono visualizzati gli errori di debug Just-In-Time per i progetti di Office. Tuttavia, è possibile abilitare questa funzionalità in modo da poter visualizzare gli errori che vengono generati. Per ulteriori informazioni, vedere [debug JIT in Visual Studio](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argomenti della riga di comando  
 Se **Azione di avvio** nella pagina delle proprietà **Debug** è impostata su **Avvia progetto**, Visual Studio non usa gli argomenti della riga di comando quando esegue il debug del progetto, anche se sono stati specificati gli argomenti della riga di comando come opzioni di avvio. Se si desidera usare gli argomenti della riga di comando quando si avvia il debug, è necessario selezionare un' **azione di avvio** diversa da **Avvia progetto**.  
  
## <a name="source-control"></a>Controllo del codice sorgente  
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. I progetti Visual Basic e C# archiviano le proprietà di debug in un file specifico dell'utente (*NomeProgetto*.vbproj.user o *NomeProgetto*.csproj.user) e questo file non è incluso nel controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.  
  
## <a name="debugging-cached-datasets-in-a-document-level-project"></a>Debug di dataset memorizzati nella cache in un progetto a livello di documento  
 Ogni volta che si compila un progetto, il dataset viene svuotato e ricreato. Se si desidera eseguire il debug di un dataset memorizzato nella cache, è necessario aprire il documento all'esterno di Visual Studio e quindi connettere il debugger.  
  
## <a name="debugging-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Debug di progetti di documento di Word in base al formato documento di Word 97-2003 (*. doc)  
 Per eseguire il debug di un progetto documento di Word basato sul formato documento di Word 97-2003 (*. doc), è necessario aggiungere la cartella del progetto all'elenco delle cartelle attendibili. Per altre informazioni sulla procedura, vedere [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
## <a name="debugging-disabled-add-ins"></a>Debug di componenti aggiuntivi disabilitati  
 Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Un'applicazione di Microsoft Office disabilita i componenti aggiuntivi VSTO per impedire che il codice con errori venga caricato ogni volta che viene avviata l'applicazione. Tuttavia, è anche facile causare un comportamento imprevisto durante il normale debug. Per informazioni su come abilitare nuovamente i componenti aggiuntivi VSTO, vedere [procedura: riabilitare un VSTO aggiuntivo che è stato disabilitato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Esistono due tipi di disabilitazione usati dalle applicazioni di Microsoft Office per i componenti aggiuntivi VSTO: disabilitazione che causa la chiusura imprevista dell'applicazione e disabilitazione che non causa la chiusura imprevista dell'applicazione.  
  
### <a name="hard-disabling"></a>Disabilitazione che causa la chiusura imprevista dell'applicazione  
 Questo tipo di disabilitazione può verificarsi quando un componente aggiuntivo VSTO causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO. In caso di disabilitazione con chiusura imprevista di un componente aggiuntivo VSTO, questo componente viene visualizzato nell'elenco **Elementi disabilitati** nell'applicazione.  
  
 Se un'applicazione di Office disabilita un componente aggiuntivo VSTO creato con gli strumenti di sviluppo di Office in Visual Studio causandone la chiusura, l'applicazione disabilita solo il componente aggiuntivo VSTO che ha causato l'errore. Gli altri componenti aggiuntivi VSTO creati usando gli strumenti di sviluppo di Office in Visual Studio per l'applicazione di Office continueranno il caricamento.  
  
### <a name="soft-disabling"></a>Disabilitazione che non causa la chiusura imprevista dell'applicazione  
 Questo tipo di disabilitazione può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe disabilitare un componente aggiuntivo VSTO senza causarne la chiusura se genera un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> . Quando un componente aggiuntivo VSTO viene disabilitato senza essere chiuso in modo imprevisto, viene visualizzato nell'elenco **Componenti aggiuntivi di applicazioni inattivi** dell'applicazione e l'applicazione modifica il valore della voce del Registro di sistema **LoadBehavior** per il componente aggiuntivo VSTO per indicare che è stato scaricato. Per ulteriori informazioni sul **LoadBehavior** voce del Registro di sistema, vedere [le voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshooting-installation-errors-by-using-the-event-viewer"></a>Risoluzione degli errori di installazione mediante il Visualizzatore eventi  
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] scrive i messaggi nel Visualizzatore eventi di Windows per tutte le eccezioni generate quando si installano o si disinstallano soluzioni Office. È possibile usare questi messaggi per risolvere i problemi di installazione e distribuzione.  
  
## <a name="troubleshooting-startup-errors-by-using-a-log-file-and-error-messages"></a>Risoluzione dei problemi di avvio usando un file di log e i messaggi di errore  
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] può scrivere tutti gli errori che si verificano durante l'avvio in un file di log o visualizzare ciascun errore in una finestra di messaggio. Per impostazione predefinita, le opzioni sono disattivate. È possibile attivare le opzioni creando le variabili di ambiente.  
  
 Per visualizzare ogni errore in una finestra di messaggio, creare una variabile di ambiente denominata `VSTO_SUPPRESSDISPLAYALERTS` e impostarla su 0 (zero). È possibile eliminare i messaggi eliminando la variabile di ambiente o impostandola su 1 (uno).  
  
 Per scrivere gli errori in un file di log, creare una variabile di ambiente denominata `VSTO_LOGALERTS` e impostarla su 1 (uno). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea il file di log nella cartella che contiene il manifesto della distribuzione per il componente aggiuntivo VSTO o nella cartella che contiene il documento o la cartella di lavoro associata alla personalizzazione. Se l'operazione non riesce, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea il file di log nella cartella %TEMP% locale. Per i componenti aggiuntivi VSTO a livello di applicazione, il nome predefinito è *nome componente aggiuntivo*.vsto.log. Per i progetti a livello di documento, il nome del file di log è *nome documento*.*estensione*.log, ad esempio ExcelWorkbook1.xlsx.log. Per arrestare la registrazione degli errori, eliminare la variabile di ambiente o impostarla su 0 (zero).  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Procedura: riabilitare un componente aggiuntivo VSTO che è stato disabilitato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  