---
title: Helper SDK per il debug | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e80344b8cec1bc013e044be39638879b049c8d0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sdk-helpers-for-debugging"></a>Helper SDK per il debug
Queste funzioni e le dichiarazioni sono funzioni di supporto globale per l'implementazione di motori di debug, analizzatori di espressioni e i provider di simboli in C++.  
  
> [!NOTE]
>  In questo momento non esistono non gestiti versioni di queste funzioni e dichiarazioni.  
  
## <a name="overview"></a>Panoramica  
 Affinché i motori di debug, analizzatori di espressioni e i provider di simboli per essere utilizzato da Visual Studio, è necessario registrarli. Questa operazione viene eseguita impostando il sottochiavi del Registro di sistema e voci, note anche come "impostazione metriche". Le funzioni globali seguenti sono progettate per semplificare il processo di aggiornamento di queste metriche. Vedere la sezione sulle posizioni del Registro di sistema per individuare il layout di ogni sottochiave del Registro di sistema che viene aggiornato da queste funzioni.  
  
## <a name="general-metric-functions"></a>Funzioni di metrica generale  
 Queste sono funzioni generali utilizzate dai motori di debug. Specifico di funzioni per gli analizzatori di espressioni e i provider di simboli sono descritte in dettaglio in un secondo momento.  
  
### <a name="getmetric-method"></a>Metodo GetMetric  
 Recupera un valore della metrica dal Registro di sistema.  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|[in] Nome di un computer remoto probabilmente verrà scritto il cui registrare (`NULL` significa che il computer locale).|  
|pszType|[in] Uno dei tipi di metrica.|  
|guidSection|[in] GUID di un modulo specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] La metrica da ottenere. Corrisponde al nome di un valore specifico.|  
|pdwValue|[in] Il percorso di archiviazione del valore dalla metrica. Esistono diverse versioni di GetMetric che può restituire un valore DWORD (come in questo esempio), BSTR, un GUID o una matrice di GUID.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per utilizzare il valore predefinito.|  
  
### <a name="setmetric-method"></a>Metodo SetMetric  
 Imposta il valore della metrica specificato nel Registro di sistema.  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|[in] Uno dei tipi di metrica.|  
|guidSection|[in] GUID di un modulo specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] La metrica da ottenere. Corrisponde al nome di un valore specifico.|  
|dwValue|[in] Il percorso di archiviazione del valore della metrica. Esistono diverse versioni di SetMetric in grado di memorizzare un valore DWORD (in questo esempio), BSTR, un GUID o una matrice di GUID.|  
|fUserSpecific|[in] TRUE se la metrica è specifico dell'utente e se deve essere scritto all'hive dell'utente anziché l'hive del computer locale.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per utilizzare il valore predefinito.|  
  
### <a name="removemetric-method"></a>Metodo RemoveMetric  
 Rimuove la metrica specificata dal Registro di sistema.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|[in] Uno dei tipi di metrica.|  
|guidSection|[in] GUID di un modulo specifico dell'analizzatore di espressioni, eccezione, e così via. Specifica una sottosezione in un tipo di metrica per un elemento specifico.|  
|pszMetric|[in] La metrica da rimuovere. Corrisponde al nome di un valore specifico.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per utilizzare il valore predefinito.|  
  
### <a name="enummetricsections-method"></a>Metodo EnumMetricSections  
 Enumera le diverse sezioni di metrica nel Registro di sistema.  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|[in] Nome di un computer remoto probabilmente verrà scritto il cui registrare (`NULL` significa che il computer locale).|  
|pszType|[in] Uno dei tipi di metrica.|  
|rgguidSections|[in, out] Preallocati matrice di GUID deve essere compilato.|  
|pdwSize|[in] Il numero massimo di GUID che può essere archiviato nel `rgguidSections` matrice.|  
|pszAltRoot|[in] Una radice del Registro di sistema alternativo da utilizzare. Impostare su `NULL` per utilizzare il valore predefinito.|  
  
## <a name="expression-evaluator-functions"></a>Funzioni dell'analizzatore di espressioni  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetEEMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveEEMetric|Rimuove la metrica specificata dal Registro di sistema.|  
|GetEEMetricFile|Ottiene un nome di file dalla metrica specificata e lo carica, restituisce il contenuto del file sotto forma di stringa.|  
  
## <a name="exception-functions"></a>Funzioni di eccezione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetExceptionMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveExceptionMetric|Rimuove la metrica specificata dal Registro di sistema.|  
|RemoveAllExceptionMetrics|Rimuove tutte le metriche di eccezione dal Registro di sistema.|  
  
## <a name="symbol-provider-functions"></a>Funzioni di Provider di simboli  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valore della metrica dal Registro di sistema.|  
|SetSPMetric|Imposta il valore della metrica specificato nel Registro di sistema.|  
|RemoveSPMetric|Rimuove la metrica specificata dal Registro di sistema.|  
  
## <a name="enumeration-functions"></a>Funzioni di enumerazione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|EnumMetricSections|Enumera tutte le metriche per un tipo di metrica specificata.|  
|EnumDebugEngine|Enumera i motori di debug registrato.|  
|EnumEEs|Enumera gli analizzatori di espressioni registrati.|  
|EnumExceptionMetrics|Enumera tutte le metriche di eccezione.|  
  
## <a name="metric-definitions"></a>Definizioni delle metriche  
 Queste definizioni utilizzabile per i nomi di metrica predefiniti. I nomi corrispondono alle diverse chiavi del Registro di sistema e i nomi dei valori e sono state definite come stringa di caratteri wide: ad esempio, `extern LPCWSTR metrictypeEngine`.  
  
|Tipi predefiniti di metrica|Descrizione: La chiave di base per...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Tutti le metriche di motore di debug.|  
|metrictypePortSupplier|Tutte le metriche di fornitore di porta.|  
|metrictypeException|Tutte le metriche di eccezione.|  
|metricttypeEEExtension|Tutte le estensioni dell'analizzatore di espressioni.|  
  
|Proprietà del motore di debug|Descrizione|  
|-----------------------------|-----------------|  
|metricAddressBP|Impostare su diverso da zero per indicare il supporto per i punti di interruzione.|  
|metricAlwaysLoadLocal|Impostare su diverso da zero per caricare sempre il motore di debug in locale.|  
|metricLoadInDebuggeeSession|NON USATO|  
|metricLoadedByDebuggee|Impostare su diverso da zero per indicare che il motore di debug verrà caricato sempre con o dal programma sottoposto a debug.|  
|metricAttach|Impostare su diverso da zero per indicare il supporto per l'allegato di programmi esistenti.|  
|metricCallStackBP|Impostare su diverso da zero per indicare il supporto dei punti di interruzione dello stack di chiamate.|  
|metricConditionalBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione condizionale.|  
|metricDataBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione sulle modifiche ai dati.|  
|metricDisassembly|Impostare su zero per indicare il supporto per la produzione di un elenco di disassembly.|  
|metricDumpWriting|Impostare su diverso da zero per indicare il supporto per i dump di scrittura (il dump di memoria da un dispositivo di output).|  
|metricENC|Impostare su zero per indicare il supporto per la modifica e continuazione. **Nota:** un motore di debug personalizzato non deve mai impostata in questo o deve sempre impostata su 0.|  
|metricExceptions|Impostare su diverso da zero per indicare il supporto per le eccezioni.|  
|metricFunctionBP|Impostare su diverso da zero per indicare il supporto per i punti di interruzione denominati (i punti di interruzione che l'interruzione quando viene chiamato un determinato nome di funzione).|  
|metricHitCountBP|Impostare su diverso da zero per indicare il supporto per l'impostazione di punti di interruzione "riscontri punto" (punti di interruzione che vengono attivati solo dopo che viene raggiunto un determinato numero di volte).|  
|metricJITDebug|Impostare su zero per indicare il supporto per il debug just-in-time (il debugger viene avviato quando si verifica un'eccezione in un processo in esecuzione).|  
|metricMemory|NON USATO|  
|metricPortSupplier|Impostare il CLSID del fornitore porta se implementata.|  
|metricRegisters|NON USATO|  
|metricSetNextStatement|Impostare su diverso da zero per indicare il supporto per l'impostazione dell'istruzione successiva (che ignora l'esecuzione di istruzioni intermedi).|  
|metricSuspendThread|Impostare su diverso da zero per indicare il supporto per sospendere l'esecuzione di thread.|  
|metricWarnIfNoSymbols|Impostare su diverso da zero per indicare che l'utente deve ricevere una notifica se sono non presenti simboli.|  
|metricProgramProvider|Impostare il CLSID del provider di programma.|  
|metricAlwaysLoadProgramProviderLocal|Impostare questa opzione a diverso da zero per indicare che il provider di programma deve sempre essere caricato in locale.|  
|metricEngineCanWatchProcess|Impostare su diverso da zero per indicare che il motore di debug controllerà per elaborare gli eventi anziché il provider di programma.|  
|metricRemoteDebugging|Impostare su diverso da zero per indicare il supporto per il debug remoto.|  
|metricEncUseNativeBuilder|Impostare questa opzione a diverso da zero per indicare che la modifica e continuazione di gestione deve usare encbuild.dll del motore di debug per compilare per la modifica e continuazione. **Nota:** un motore di debug personalizzato non deve mai impostata in questo o deve sempre impostata su 0.|  
|metricLoadUnderWOW64|Impostare questa proprietà su diverso da zero per indicare che il motore di debug deve essere caricato nel processo oggetto del debug in WOW durante il debug di un processo a 64 bit. in caso contrario, il motore di debug verrà caricato nel processo di Visual Studio (che è in esecuzione in WOW64).|  
|metricLoadProgramProviderUnderWOW64|Impostare questa proprietà su diverso da zero per indicare che il provider del programma deve essere caricato nel processo oggetto del debug durante il debug di un processo a 64 bit in WOW; in caso contrario, verrà caricato nel processo di Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Impostare su diverso da zero per indicare che il processo deve essere arrestata se viene generata un'eccezione non gestita oltre i limiti gestiti/non gestiti non di codice.|  
|metricAutoSelectPriority|Impostare una priorità per la selezione automatica del motore di debug (più valori è uguale a priorità più alta).|  
|metricAutoSelectIncompatibleList|Chiave del Registro di sistema contenente le voci che specificano i GUID per motori di debug da ignorare nella selezione automatica. Queste voci sono un numero (0, 1, 2 e così via) con un GUID espresso come stringa.|  
|metricIncompatibleList|Chiave del Registro di sistema contenente le voci che specificano i GUID per i motori di debug che non sono compatibili con il motore di debug.|  
|metricDisableJITOptimization|Impostare su diverso da zero per indicare che devono essere disabilitate le ottimizzazioni di just-in-time (per il codice gestito) durante il debug.|  
  
|Proprietà dell'analizzatore di espressioni|Descrizione|  
|-------------------------------------|-----------------|  
|metricEngine|Questo contiene il numero di motori di debug che supportano l'analizzatore di espressioni specificato.|  
|metricPreloadModules|Impostare su diverso da zero per indicare che devono essere precaricati moduli quando viene avviato un analizzatore di espressioni in un programma.|  
|metricThisObjectName|Impostare il nome dell'oggetto "this".|  
  
|Proprietà di estensione dell'analizzatore di espressioni|Descrizione|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nome della dll che supporta questa estensione.|  
|metricExtensionRegistersSupported|Elenco di registri supportati.|  
|metricExtensionRegistersEntryPoint|Punto di ingresso per l'accesso ai registri.|  
|metricExtensionTypesSupported|Elenco di tipi supportati.|  
|metricExtensionTypesEntryPoint|Punto di ingresso per l'accesso a tipi.|  
  
|Proprietà porta di fornitore|Descrizione|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Il CLSID del selettore porta (una finestra di dialogo l'utente può utilizzare per selezionare le porte e aggiungere porte da utilizzare per il debug).|  
|metricDisallowUserEnteredPorts|Diverso da zero se non è possibile aggiungere le porte immesso dall'utente per il fornitore della porta (in questo modo la finestra di dialogo di selezione porta essenzialmente di sola lettura).|  
|metricPidBase|L'ID di processo di base utilizzata dal fornitore porta durante l'allocazione di ID di processo.|  
  
|Tipi di archivio predefiniti SP|Descrizione|  
|-------------------------------|-----------------|  
|storetypeFile|I simboli vengono archiviati in un file separato.|  
|storetypeMetadata|I simboli vengono archiviati come metadati in un assembly.|  
  
|Varie proprietà|Descrizione|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Impostare su diverso da zero per visualizzare il codice nonuser.|  
|metricJustMyCodeStepping|Impostare su diverso da zero per indicare che l'esecuzione di istruzioni può trovarsi solo nel codice utente.|  
|metricCLSID|CLSID di un oggetto di un tipo specifico di metrica.|  
|metricName|Nome descrittivo per un oggetto di un tipo specifico di metrica.|  
|metricLanguage|Nome della lingua.|  
  
## <a name="registry-locations"></a>Percorsi del Registro di sistema  
 Le metriche sono leggervi e scritte nel Registro di sistema, in particolare nel `VisualStudio` sottochiave.  
  
> [!NOTE]
>  La maggior parte dei casi, verranno scritto le metriche chiave HKEY_LOCAL_MACHINE. Tuttavia, talvolta HKEY_CURRENT_USER sarà la chiave di destinazione. Dbgmetric.lib gestisce entrambe le chiavi. Quando si recupera una metrica, viene eseguita la ricerca HKEY_CURRENT_USER prima, quindi HKEY_LOCAL_MACHINE. Quando viene impostata una metrica, un parametro specifica la chiave di primo livello da utilizzare.  
  
 *[chiave del Registro di sistema]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[radice versione]*\  
  
 *[radice metrica]*\  
  
 *[tipo di metrica]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[chiave del Registro di sistema]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*[radice versione]*|La versione di Visual Studio (ad esempio, `7.0`, `7.1`, o `8.0`). Tuttavia, questa radice può anche essere modificata utilizzando il **/rootsuffix** passa a **devenv.exe**. Per VSIP, è in genere questo modificatore **Exp**, pertanto la radice di versione è, ad esempio, 8.0Exp.|  
|*[radice metrica]*|Il valore può essere `AD7Metrics` o `AD7Metrics(Debug)`, a seconda se viene utilizzata la versione di debug di dbgmetric.lib. **Nota:** dbgmetric.lib viene utilizzato, o meno questa convenzione di denominazione deve essere rispettata nel caso di differenze tra debug e rilascio versioni che devono essere riflessa nel Registro di sistema.|  
|*[tipo di metrica]*|Il tipo di metrica da scrivere: `Engine`, `ExpressionEvaluator`, `SymbolProvider`e così via. Questi sono tutti definiti come dbgmetric.h come `metricTypeXXXX`, dove `XXXX` è il nome del tipo specifico.|  
|*[metrica]*|Il nome di una voce per assegnare un valore per impostare la metrica. L'organizzazione delle metriche effettivo dipende dal tipo metrica.|  
|*[valore della metrica]*|Il valore assegnato alla metrica. Il tipo che di valore deve avere (stringa), numero, via varia a seconda della metrica.|  
  
> [!NOTE]
>  Tutti i GUID vengono archiviati nel formato `{GUID}`. Ad esempio `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Motori di debug  
 Di seguito è l'organizzazione delle metriche di motori di debug nel Registro di sistema. `Engine` è il nome del tipo di metrica per un motore di debug e corrisponde a *[tipo di metrica]* nel sottoalbero del Registro di sistema precedente.  
  
 `Engine`\  
  
 *[motore guid]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `PortSupplier`\  
  
 `0` = *[guid fornitore porta]*  
  
 `1` = *[guid fornitore porta]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[motore guid]*|Il GUID del motore di debug.|  
|*[classe guid]*|Il GUID della classe che implementa questo motore di debug.|  
|*[guid fornitore porta]*|Il GUID del fornitore porta, se presente. Numero di motori di debug utilizza il fornitore della porta predefinita e non si specifica proprio fornitore. In questo caso, la sottochiave `PortSupplier` sarà presente.|  
  
### <a name="port-suppliers"></a>Fornitori di porte  
 Di seguito è l'organizzazione delle metriche di fornitore di porta nel Registro di sistema. `PortSupplier` è il nome del tipo di metrica per un fornitore di porta e corrisponde a *[tipo di metrica]*.  
  
 `PortSupplier`\  
  
 *[guid fornitore porta]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid fornitore porta]*|Il GUID del fornitore porta|  
|*[classe guid]*|Il GUID della classe che implementa il fornitore della porta|  
  
### <a name="symbol-providers"></a>Provider di simboli  
 Di seguito è l'organizzazione delle metriche fornitore simbolo nel Registro di sistema. `SymbolProvider` è il nome del tipo di metrica per il provider di simboli e corrisponde a *[tipo di metrica]*.  
  
 `SymbolProvider`\  
  
 *[guid provider simbolo]*\  
  
 `file`\  
  
 `CLSID` = *[classe guid]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `metadata`\  
  
 `CLSID` = *[classe guid]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid provider simbolo]*|Il GUID del provider di simboli|  
|*[classe guid]*|Il GUID della classe che implementa il provider di simboli|  
  
### <a name="expression-evaluators"></a>Analizzatori di espressioni  
 Di seguito è l'organizzazione delle metriche dell'analizzatore di espressioni nel Registro di sistema. `ExpressionEvaluator` è il nome del tipo di metrica per l'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
> [!NOTE]
>  Il tipo di metrica per `ExpressionEvaluator` non è definito in dbgmetric.h, come si presuppone che tutte le modifiche alla metrica per gli analizzatori di espressioni verranno esaminate le funzioni di metrica dell'analizzatore di espressioni espressione appropriata (il layout del `ExpressionEvaluator` sottochiave è più o meno complicata, pertanto i dettagli sono nascosti all'interno di dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[guid language]*\  
  
 *[guid fornitore]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 `Engine`\  
  
 `0` = *[guid motore di debug]*  
  
 `1` = *[guid motore di debug]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid language]*|Il GUID di una lingua|  
|*[guid fornitore]*|Il GUID di un fornitore|  
|*[classe guid]*|Il GUID della classe che implementa l'analizzatore di espressioni|  
|*[guid motore di debug]*|Il GUID di un motore di debug che con l'analizzatore di espressioni|  
  
### <a name="expression-evaluator-extensions"></a>Estensioni dell'analizzatore di espressioni  
 Di seguito è l'organizzazione delle metriche di estensione dell'analizzatore di espressioni nel Registro di sistema. `EEExtensions` è il nome del tipo di metrica per l'espressione estensioni dell'analizzatore di espressioni e corrisponde a *[tipo di metrica]*.  
  
 `EEExtensions`\  
  
 *[guid estensione]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid estensione]*|Il GUID di un'estensione dell'analizzatore di espressioni|  
  
### <a name="exceptions"></a>Eccezioni  
 Di seguito è l'organizzazione delle metriche delle eccezioni nel Registro di sistema. `Exception` è il nome del tipo di metrica per le eccezioni e corrisponde a *[tipo di metrica]*.  
  
 `Exception`\  
  
 *[guid motore di debug]*\  
  
 *[tipi di eccezione]*\  
  
 *[eccezione]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
 *[eccezione]*\  
  
 *[metrica] = [valore della metrica]*  
  
 *[metrica] = [valore della metrica]*  
  
|Segnaposto|Descrizione|  
|-----------------|-----------------|  
|*[guid motore di debug]*|Il GUID di un motore di debug che supporta le eccezioni.|  
|*[tipi di eccezione]*|Un titolo generale per la sottochiave che identifica la classe di eccezioni che possono essere gestiti. I nomi tipici sono **le eccezioni C++**, **le eccezioni Win32**, **eccezioni Common Language Runtime**, e **dei controlli runtime nativo**. Questi nomi vengono usati anche per identificare una classe di eccezione per l'utente specifica.|  
|*[eccezione]*|Un nome per un'eccezione: ad esempio, **com_error** o **CTRL-INTER**. Questi nomi vengono usati anche per identificare una particolare eccezione all'utente.|  
  
## <a name="requirements"></a>Requisiti  
 Questi file si trovano nel [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] directory di installazione SDK (per impostazione predefinita, *[unità]*\Programmi\Microsoft Visual Studio 2010 SDK\\).  
  
 Intestazione: includes\dbgmetric.h  
  
 Libreria: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)