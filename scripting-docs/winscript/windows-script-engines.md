---
title: Motori di Windows Script | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2191b8e76e2b96d05633156d09a08b5416faae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-engines"></a>Motori di script Windows
Per implementare un motore di Windows Script di Microsoft, creare un oggetto COM OLE che supporta le interfacce seguenti.  
  
|||  
|-|-|  
|Interfaccia|Descrizione|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Offre la capacità di scripting di base. L'implementazione di tale interfaccia è necessaria.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Offre la capacità di aggiungere testo dello script, valutare le espressioni e così via. L'implementazione di questa interfaccia è facoltativa: tuttavia, se non è implementata, il motore dello script deve implementare una delle interfacce IPersist* per caricare uno script.|  
|IPersist *|Fornisce il supporto di persistenza. L'implementazione di almeno una delle interfacce seguenti è necessaria se [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) non è implementata.<br /><br /> IPersistStorage: offre il supporto l'attributo DATA = {url} nel tag OBJECT.<br /><br /> IPersistStreamInit: offre il supporto per lo stesso di `IPersistStorage` e per l'attributo DATA="flusso di byte codificato in formato stringa" nel tag OBJECT.<br /><br /> IPersistPropertyBag: offre il supporto l'attributo PARAM= nel tag OBJECT.|  
  
> [!NOTE]
>  È possibile che il motore di scripting non verrà mai chiamato al momento di salvare o ripristinare uno stato di script tramite `IPersist*`. In alternativa, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) viene usato chiamando [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) per creare uno script vuoto, quindi gli scriptlet vengono aggiunti e connessi agli eventi con [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) e viene aggiunto un codice generale con [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Ciononostante, un motore di scripting deve implementare completamente almeno un'interfaccia `IPersist*` (preferibilmente `IPersistStreamInit`), in quanto altre applicazioni host potrebbero tentare di usarle.  
  
 Le sezioni seguenti descrivono l'implementazione di un motore di Scripting di Windows in modo più dettagliato.  
  
 Vedere i [Riferimenti sulle interfacce Windows Script](../winscript/reference/windows-script-interfaces-reference.md) per altre informazioni.  
  
## <a name="registry-standard"></a>Standard del Registro di sistema  
 Un motore di Script di Windows consente di identificare se stesso tramite gli identificatori di categoria. Lo script di Windows attualmente definisce due identificatori di categoria.  
  
|||  
|-|-|  
|Categoria|Descrizione|  
|CATID_ActiveScript|Indica che gli identificatori di classe (CLSID) sono i motori di Script di Windows che supportano, come minimo, l'interfaccia [IActiveScript](../winscript/reference/iactivescript.md) e un meccanismo di persistenza (il `IPersistStorage`, `IPersistStreamInit`, o l'interfaccia IPersistPropertyBag).|  
|CATID_ActiveScriptParse|Indica che i CLSID sono motori di Script di Windows che supportano, come minimo, le interfacce [IActiveScript](../winscript/reference/iactivescript.md) e [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
  
 Anche se [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) non è un meccanismo di persistenza true, supporta comunque il metodo [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) che è funzionalmente equivalente a `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Stati del motore di script  
 In qualsiasi momento, un motore dello Script di Windows può essere in uno dei diversi stati.  
  
|||  
|-|-|  
|Stato|Descrizione|  
|non inizializzato|Lo script non è stato inizializzato o caricato tramite un'interfaccia IPersist*, o non dispone di un set di interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md). Il motore di scripting in genere non è utilizzabile da questo stato finché lo script non viene caricato.|  
|inizializzato|Lo script è stato inizializzato con un'interfaccia `IPersist*` e ha un set di interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md), ma non è connesso a oggetti host ed eventi di sink. Si noti che questo stato indica semplicemente che il metodo `IPersist*::Load`, `IPersist*::InitNew`, o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) è stato completato e che il metodo [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) è stato chiamato. Il motore non può eseguire il codice in questa modalità. Il codice delle code del motore in cui passa l'host attraverso il metodo [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) esegue il codice dopo la transizione nello stato di avvio.<br /><br /> Poiché linguaggi possono variare notevolmente in semantica, i motori di scripting non devono supportare necessariamente la transizione di stato. I motori che supportano il metodo [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) devono, tuttavia, supportare la transizione di stato. Gli host si devono preparare per la transizione e intraprendere l'azione appropriata: rilasciare il motore di scripting corrente, creare un nuovo motore di scripting e chiamare `IPersist*::Load`, `IPersist*::InitNew`, o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (ed eventualmente chiamare anche [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). L'uso di questa transizione deve essere considerato come un'ottimizzazione della procedura precedente. Si noti che tutte le informazioni che il motore di scripting ha ottenuto circa i nomi degli elementi denominati e le informazioni sul tipo che descrivono gli elementi denominati rimangono valide.<br /><br /> Poiché i linguaggi variano notevolmente, la definizione della semantica esatta di questa transizione è difficile. Come minimo, il motore di scripting deve disconnettersi da tutti gli eventi e rilasciare tutti i puntatori SCRIPTINFO_IUNKNOWN ottenuti chiamando il metodo [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md). Il motore deve ottenere nuovamente questi puntatori dopo che lo script viene eseguito di nuovo. Il motore di scripting deve inoltre ripristinare lo script in uno stato iniziale che sia appropriato per la lingua. VBScript, per esempio, reimposta tutte le variabili e mantiene i codici aggiunti in modo dinamico mediante una chiamata [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) con il set di flag SCRIPTTEXT_ISPERSISTENT. Altri linguaggi potrebbero dover mantenere i valori correnti (ad esempio Lisp poiché non c'è alcuna separazione di codice/dati) o reimpostare uno stato noto (che include i linguaggi con le variabili inizializzate in modo statico).<br /><br /> Si noti che la transizione allo stato avviato deve avere la stessa semantica (vale a dire deve lasciare il motore di scripting nello stesso stato) della chiamata IPersist*::Save per salvare il motore di scripting, e quindi chiamare IPersist\*::Load per caricare un nuovo motore di scripting; queste azioni devono avere la stessa semantica di [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). I motori di scripting che non supportano ancora IActiveScript::Clone o `IPersist*` devono valutare attentamente il comportamento della transizione allo stato avviato, in modo che tale transizione non violi le condizioni indicate in precedenza se IActiveScript::Clone o il supporto `IPersist*` è stato aggiunto in un secondo momento.<br /><br /> Durante tale transizione allo stato avviato, il motore di scripting verrà disconnesso dai sink dell'evento dopo che i distruttori appropriati e così via vengono eseguiti nello script. Per evitare che questi distruttori vengano eseguiti, l'host può innanzitutto spostare lo script nello stato di disconnessione prima di spostarlo nello stato avviato.<br /><br /> Usare [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread dello script in esecuzione senza attendere gli eventi correnti e così via, per completare l'esecuzione.|  
|avviata|La transizione dallo stato inizializzato allo stato avviato fa sì che il motore esegua qualsiasi codice accodato nello stato non inizializzato. Il motore può eseguire il codice mentre è in stato avviato, ma non è connesso a tutti gli eventi aggiunti tramite il metodo [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md). Il motore può eseguire il codice chiamando l'interfaccia IDispatch ottenuta dal metodo [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md), oppure chiamando [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). È possibile che l'ulteriore inizializzazione di sfondo (caricamento progressivo) sia ancora in corso e che la chiamata del metodo [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) con il set di flag SCRIPTSTATE_CONNECTED possa provocare l'arresto dello script fino a quando l'inizializzazione non è completa.|  
|connesso|Lo script è caricato e connesso agli eventi di sink da oggetti dell'host. Se si tratta di una transizione dallo stato inizializzato, il motore di scripting deve passare tramite questo stato avviato, eseguire le operazioni necessarie, prima di immettere lo stato di connessione e la connessione agli eventi.|  
|disconnesso|Lo script viene caricato e ha uno stato in fase di esecuzione, ma è temporaneamente disconnesso dagli eventi di sink dagli oggetti dell'host. Questo può avvenire in modo logico (ignorando gli eventi ricevuti) o fisico (chiamando IConnectionPoint:: Unadvise nei punti di connessione appropriati). Se si tratta di una transizione dallo stato inizializzato, il motore di scripting deve passare tramite questo stato avviato, eseguire le operazioni necessarie, prima di immettere lo stato di disconnessione. I sink dell'evento che sono in corso vengono completati prima che lo stato cambi (usare [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread dello script in esecuzione). Questo stato si distingue dallo stato inizializzato in quanto la transizione a questo stato non determina il ripristino dello script, lo stato di runtime dello script non viene reimpostato e non viene eseguita una procedura di inizializzazione dello script.|  
|chiuso|Lo script è stato chiuso. Il motore di scripting non funziona più e restituisce gli errori per la maggior parte dei metodi.|  
  
 Nella figura seguente vengono mostrate le relazioni tra i vari stati del motore di scripting e vengono illustrati i metodi che causano le transizioni da uno stato all'altro.  
  
 Nella figura seguente vengono illustrate le azioni che il motore di scripting esegue durante le varie transizioni di stato.  
  
## <a name="scripting-engine-threading"></a>Threading del motore di scripting  
 Poiché un motore di scripting di Windows può essere usato in molti ambienti, è importante mantenere il suo modello di esecuzione il più possibile flessibile. Ad esempio, un host basato su server potrebbe dover mantenere una progettazione multithreading durante l'uso di Windows Script in modo efficiente. Allo stesso tempo, un host che non usa il threading, ad esempio un'applicazione tipica, non deve essere sovraccaricato con la gestione del threading. Windows Script consente di ottenere questo equilibrio limitando i modi in cui un motore di scripting a thread libero può richiamare l'host, liberando gli host da questo carico di lavoro.  
  
 I motori di scripting usati nei server vengono in genere implementati come oggetti COM a threading libero. Ciò significa che i metodi sull'interfaccia [IActiveScript](../winscript/reference/iactivescript.md) e le relative interfacce associate possono essere chiamati da qualsiasi thread del processo, senza effettuare il marshalling. (Sfortunatamente, questo significa anche che il motore di scripting deve essere implementato come un server in-process, in quanto OLE attualmente non supporta il marshalling di interprocesso degli oggetti a thread libero.) La sincronizzazione è di responsabilità del motore di scripting. Per i motori di scripting che non sono rientranti internamente, o per i modelli di linguaggio che non hanno subito il multithreading, la sincronizzazione potrebbe essere semplice come la serializzazione dell'accesso al motore di scripting con un mutex. Naturalmente determinati metodi, ad esempio [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), non devono essere serializzati in questo modo, in modo che uno script bloccato possa essere completato da un altro thread.  
  
 Il fatto che [IActiveScript](../winscript/reference/iactivescript.md) sia in genere a thread libero implica che l'interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) e il modello oggetto dell'host debbano essere anch'essi a thread libero. Ciò rende l'implementazione dell'host abbastanza complessa, in particolare nel caso comune in cui l'host sia un'applicazione basata su Windows a thread singolo con i controlli ActiveX del modello appartamento a thread singolo nel modello dell'oggetto. Per questo motivo, vengono inseriti i vincoli seguenti sull'utilizzo del motore di scripting di [IActiveScriptSite](../winscript/reference/iactivescriptsite.md):  
  
 Il sito dello script viene sempre chiamato nel contesto di un thread dell'host. Vale a dire che la creazione del motore di scripting non chiama mai il sito dello script nel contesto di un thread che è stato creato dal motore di scripting, ma solo dall'interno di un metodo del motore di scripting che è stato chiamato dall'host tramite [IActiveScript](../winscript/reference/iactivescript.md) e i suoi derivati, tramite l'oggetto di distribuzione del motore di scripting esposto, tramite un messaggio di Windows o da un'origine di evento nel modello dell'oggetto dell'host.  
  
 Il sito dello script non viene mai chiamato dall'interno del contesto di un metodo di controllo dello stato semplice del thread (ad esempio, il metodo [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)) o dal metodo [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Windows Script](../winscript/windows-script-interfaces.md)