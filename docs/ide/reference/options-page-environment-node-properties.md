---
title: Pagina delle opzioni, Proprietà del nodo Ambiente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cd05ebf4c0161611789214295003eced4ca0d4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-page-environment-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Ambiente
Questo documento descrive le pagine, o raccolte di proprietà, associate alla categoria **Ambiente**, `DTE.Properties("Environment", <Property Page>)`, della finestra di dialogo **Opzioni**. Il titolo di ogni sottosezione rappresenta la chiamata usata per accedere alla raccolta Proprietà e la tabella di ogni sottosezione elenca le proprietà della raccolta.  
  
## <a name="general"></a>Generale  
 `DTE.Properties("Environment", "General")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|ShowStatusBar|Get/Set (Boolean)|Determina se viene visualizzata o meno la barra di stato.|  
|WindowMenuContainsNItems|Get/Set (Short)|Determina la modalità di contenimento delle finestre di documento nella parte inferiore del menu Finestre.|  
|MRUListContainsNItems|Get/Set (Short)|Determina il numero dei file visualizzati nel sottomenu "Usati di recente".|  
|Animations|Get/Set (Boolean)|Determina se l'ambiente di sviluppo integrato (IDE, Integrated Development Environment) usa l'animazione nella barra di stato.|  
|AnimationSpeed|Get/Set (Short)||  
|AutoAdjustExperience|Get/Set (Boolean)|Regola automaticamente l'esperienza visiva in base alle prestazioni del client.|  
|RichClientExperienceOptions|Get/Set (Enum)|Abilita l'esperienza visiva dettagliata del client con i valori presenti in <xref:EnvDTE100.vsRichClientExperienceOptions>.|  
|CloseButtonActiveTabOnly|Get/Set (Boolean)|Determina se il pulsante **Chiudi** viene visualizzato solo nella scheda attiva.|  
|AutohidePinActiveTabOnly|Get/Set (Boolean)|Determina se il pulsante **Nascondi automaticamente** ha effetto solo sulla scheda attiva.|  
  
## <a name="add-inmacros-security"></a>Sicurezza macro/componenti aggiuntivi  
 `DTE.Properties("Environment", "AddinMacrosSecurity")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|MacrosEnabled|Get/Set (Boolean)|Consente l'esecuzione delle macro.|  
|AddinsEnabled|Get/Set (Boolean)|Consente il caricamento dei componenti aggiuntivi.|  
|LoadAddinsFromTheWeb|Get/Set (Boolean)|Consente il caricamento dei componenti aggiuntivi da un URL nel Web.|  
  
## <a name="documents"></a>Documenti  
 `DTE.Properties("Environment", "Documents")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|ReuseSavedActiveDocWindow|Get/Set (Boolean)|Determina se la finestra del documento corrente verrà riutilizzata per l'apertura di un nuovo file se il documento corrente viene salvato. `false` indica di aprire sempre una nuova finestra per ogni documento aperto.|  
|DetectFileChangesOutsideIDE|Get/Set (Boolean)|Determina se l'ambiente ricarica automaticamente i file aperti nell'IDE quando il sistema operativo notifica all'IDE che i file sono stati modificati su disco.|  
|AutoloadExternalChanges|Get/Set (Boolean)|Determina se le modifiche esterne rilevate nei documenti aperti causano il caricamento automatico del file modificato se il documento aperto non viene modificato. Se il documento aperto viene modificato e questa proprietà è `true`, l'IDE si comporta come se questa proprietà fosse `false`.|  
|InitializeOpenFileFromCurrentDocument|Get/Set (Boolean)|Determina se il comando <xref:EnvDTE.DTEClass.OpenFile%2A> definisce la directory e il nome file dall'ultimo documento attivo o dall'ultima posizione in cui è stato aperto un file.|  
|MiscFilesProjectSavesLastNItems|Get/Set (Short)|Determina il numero di file archiviati nel progetto File esterni. Di conseguenza, al successivo uso dell'IDE sarà possibile visualizzare gli ultimi elementi aperti come file esterni su disco.|  
|ShowMiscFilesProject|Get/Set (Boolean)|Determina se il progetto File esterni viene visualizzato.|  
|CheckForConsisentLineEndings|Get/Set (Boolean)|Verifica la coerenza delle terminazioni riga al caricamento del file.|  
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boolean)|Salva i documenti come Unicode quando i dati non possono essere salvati nella tabella codici.|  
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boolean)|Visualizza un avviso se l'annullamento globale avrà effetto su altri file modificati.|  
|AllowEditingReadOnlyFiles|Get/Set (Boolean)|Consente di modificare i file di sola lettura, ma visualizza un avviso quando viene effettuato un tentativo di salvataggio di tali file.|  
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Posizione nella scheda in cui inserire il documento aperto.|  
  
## <a name="extension-manager"></a>Gestione estensioni  
 `DTE.Properties("Environment", "ExtensionManager")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|EnableAdminExtensions|Get/Set (Boolean)|Carica le estensioni per utente quando Visual Studio viene eseguito con credenziali di amministratore. Dopo la modifica di questo valore, è necessario riavviare Visual Studio.|  
|EnableOnline|Get/Set (Boolean)|Consente l'accesso alle estensioni di Visual Studio Marketplace.|  
|AutomaticallyCheckForUpdates|Get/Set (Boolean)|Controlla automaticamente la presenza di aggiornamenti per le estensioni installate.|  
  
## <a name="find-and-replace"></a>Trova e sostituisci  
 `DTE.Properties("Environment", "FindAndReplace")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|ShowWarningMessages|Get/Set (Boolean)|Visualizza messaggi di avviso.|  
|InitializeFromEditor|Get/Set (Boolean)|Inserisce automaticamente il testo dell'editor nella casella **Trova**.|  
|ShowMessageBoxes|Get/Set (Boolean)|Visualizza messaggi informativi.|  
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boolean)|Nasconde la finestra **Trova e sostituisci** quando viene trovata una corrispondenza con **Ricerca veloce** o **Sostituzione veloce**.|  
  
## <a name="import-and-export-settings"></a>Importa/Esporta impostazioni  
 `DTE.Properties("Environment", "Import and Export Settings")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|TrackTeamSettings|Get/Set (Boolean)|Usa le impostazioni nel file specificato da TeamSettingsFile.|  
|TeamSettingsFile|Get/Set (String)|Nome del file che include le impostazioni del team.|  
|AutoSaveFile|Get/Set (String)|Nome del file in cui le impostazioni utente vengono salvate automaticamente.|  
  
## <a name="international-settings"></a>Impostazioni internazionali  
 `DTE.Properties("Environment", "International")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|Linguaggio|Get/Set (String)|Valore LCID per la lingua corrente per Visual Studio.|  
  
## <a name="keyboard"></a>Tastiera  
 `DTE.Properties("Environment", "Keyboard")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|Scheme|Get/Set (String)|Restituisce una stringa contenente uno schema predefinito, una stringa contenente il percorso completo del file con estensione vsk caricato o "(Predefinito)" se non viene caricato alcun file con estensione vsk.|  
  
## <a name="projects-and-solution"></a>Progetti e soluzioni  
 `DTE.Properties("Environment", "ProjectsAndSolution")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|OnRunOrPreview|Get/Set (String)|Determina se l'IDE salva tutto prima dell'anteprima o dell'esecuzione di un progetto compilato.|  
|ProjectsLocation|Get/Set (String)|Determina la directory predefinita in cui i nuovi progetti vengono salvati dalla finestra di dialogo **Aggiungi progetto**.|  
|ShowOutputWindowBeforeBuild|Get/Set (Boolean)|Determina se all'avvio di una compilazione viene visualizzata la finestra **Output**.|  
|ShowTaskListAfterBuild|Get/Set (Boolean)|Determina se, a seguito di un'operazione di compilazione non riuscita, viene visualizzato l'**Elenco attività** dopo la compilazione.|  
|TrackFileSelectionInExplorer|Get/Set (Boolean)|Determina se in **Esplora soluzioni** viene tenuta traccia dell'elemento corrente.|  
|AlwaysShowSolutionNode|Get/Set (Boolean)|Determina se il nodo della soluzione viene visualizzato o meno.|  
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boolean)|Determina se le operazioni di salvataggio sono limitate ai progetti di avvio e ai relativi file dipendenti.|  
|ShowAdvancedBuildConfigurations|Get/Set (Boolean)|Determina se le configurazioni della build avanzate vengono visualizzate o meno.|  
|ConcurrentBuilds|Get/Set (String)|Determina il numero massimo di compilazioni di progetto parallele che possono verificarsi.|  
|SaveNewProjects|Get/Set (Boolean)|Determina se i nuovi progetti vengono salvati automaticamente dopo la creazione.|  
|PromptForRenameSymbol|Get/Set (Boolean)|Specifica se richiedere la ridenominazione simbolica quando i file vengono rinominati.|  
|OnRunWhenErrors|Get/Set (Enum)|Specifica il comportamento o l'esecuzione in caso di una compilazione completata con errori.|  
|OnRunWhenOutOfDate|Get/Set (Enum)|Specifica il comportamento o l'esecuzione per un progetto non aggiornato.|  
|ProjectTemplatesLocation|Get/Set (String)|Directory contenente i modelli di progetto utente.|  
|ProjectItemTemplatesLocation|Get/Set (String)|Directory contenente i modelli di elemento utente.|  
|DefaultBehaviorForStartupProjects|Get/Set (String)||  
|MSBuildOutputVerbosity|Get/Set (String)|Specifica il livello di dettaglio dell'output di compilazione.|  
  
## <a name="startup"></a>Avvio  
 `DTE.Properties("Environment", "Startup")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|OnStartUp|Get/Set (Enum)|Azione da eseguire all'avvio, da <xref:EnvDTE.vsStartUp>, con valori compresi tra 0 e 5:<br /><br /> - 0: Apri home page<br />- 1: Carica ultima soluzione caricata<br />- 2: Mostra finestra **Apri progetto**<br />- 3: Mostra finestra **Nuovo progetto**<br />- 4: Visualizza ambiente vuoto<br />- 5: Mostra pagina iniziale|  
|StartPageRSSUrl|Get/Set (String)|URL del feed RSS usato all'avvio.|  
|StartPageRefreshDownloadedContent|Get/Set (Boolean)|Aggiorna la pagina iniziale dopo ogni passaggio dell'intervallo specificato in StartPageRefreshInterval.|  
|StartPageRefreshInterval|Get/Set (Short)|Intervallo in minuti per l'aggiornamento della pagina iniziale.|  
  
## <a name="tasklist"></a>TaskList  
 `DTE.Properties("Environment", "TaskList")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|ConfirmTaskDeletion|Get/Set (Boolean)|Specifica se viene visualizzata una finestra di conferma quando si eliminano attività dall'**Elenco attività**.|  
|WarnOnAddingHiddenItem|Get/Set (Boolean)|Specifica se viene visualizzato un avviso all'aggiunta di un'attività definita dall'utente che non verrà visualizzata.|  
|DontShowFilePaths|Get/Set (Boolean)|Specifica se mostrare i percorsi dei file completi nell'Elenco attività.|  
|CommentTokens|SafeArray|Restituisce un SafeArray di valori token di commento. Ognuno presenta i campi `Name` (stringa) e `Priority` (<xref:EnvDTE.vsTaskPriority>, alta, media o bassa).|  
  
## <a name="web-browser"></a>Web browser  
 `DTE.Properties("Environment", "WebBrowser")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|HomePage|Get/Set (String)|Rappresenta l'URL della home page.|  
|SearchPage|Get/Set (String)|Rappresenta l'URL della pagina di ricerca.|  
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Source, Design, External).|  
|ViewSourceExternalProgram|Get/Set (String)|Il percorso del visualizzatore del codice sorgente esterno.|  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo delle impostazioni relative alle opzioni](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Pagina delle opzioni, Proprietà del nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)