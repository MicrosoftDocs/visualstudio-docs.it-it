---
title: Interfacce Windows Script | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200a1ac1bf273e2515e1e17b6f83c2020ff9884d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-interfaces"></a>Interfacce Windows Script
Le interfacce Microsoft Windows Script consentono a un'applicazione di aggiungere script e automazione OLE. Gli host di scripting basati su Windows Script possono usare motori di script provenienti da più origini e fornitori per la gestione di script tra i componenti. L'implementazione dello script (lingua, sintassi, formato persistente, modello di esecuzione e così via) viene lasciata al fornitore dello script.  
  
 La documentazione di Windows Script è suddivisa nelle sezioni seguenti:  
  
 [Host Windows Script](../winscript/windows-script-hosts.md)  
  
 [Motori Windows Script](../winscript/windows-script-engines.md)  
  
 [Panoramica del debug di script ActiveX](../winscript/active-script-debugging-overview.md)  
  
 [Panoramica della profilatura di script ActiveX](../winscript/active-script-profiling-overview.md)  
  
 [Riferimenti sulle interfacce Windows Script](../winscript/reference/windows-script-interfaces-reference.md)  
  
## <a name="windows-script-background"></a>Contesto di Windows Script  
 Le interfacce di Windows Script rientrano in due categorie: host e motori di Windows Script. Un host consente di creare un motore di script e chiama il motore per eseguire gli script. Esempi di host di Windows Script:  
  
-   Microsoft Internet Explorer  
  
-   Strumenti di creazione Internet  
  
-   Shell  
  
 I motori di Windows Script possono essere sviluppati per qualsiasi lingua o ambiente di runtime, tra cui:  
  
-   Microsoft Visual Basic Scripting Edition (VBScript)  
  
-   Perl  
  
-   Lisp  
  
 Per aumentare al massimo la flessibilità dell'implementazione dell'host, viene offerto un wrapper di automazione OLE per Windows Script. Un host che usa questo oggetto wrapper per creare un'istanza di motore di script non possiede tuttavia il livello di controllo sullo spazio dei nomi in fase di esecuzione, il modello di persistenza, e così via, che avrebbe se usasse direttamente Windows Script.  
  
 La progettazione di Windows Script consente di isolare gli elementi dell'interfaccia richiesti solo in un ambiente di creazione in modo che gli host non di creazione (ad esempio, browser e visualizzatori) e i motori di script (ad esempio, VBScript) possano essere mantenuti leggeri.  
  
## <a name="windows-script-basic-architecture"></a>Architettura di base di Windows Script  
 Nella figura seguente viene illustrata l'interazione tra un host di Windows Script e un motore di Windows Script.  
  
 I passaggi necessari per l'interazione tra l'host e il motore figurano nell'elenco seguente.  
  
1.  Creare un progetto. L'host carica un progetto o documento. (Questo passaggio non è specifico di Windows Script, ma è incluso di seguito per completezza.)  
  
2.  Creare il motore di Windows Script. L'host chiama `CoCreateInstance` per creare un nuovo motore di Windows Script, che specifica l'identificatore di classe (CLSID) del motore di script specifico da usare. Ad esempio, il browser HTML di Internet Explorer riceve l'identificatore di classe del motore di script tramite il CLSID = attributo del tag HTML \<OBJECT>.  
  
3.  Caricare lo script. Se il contenuto dello script è stato reso persistente, l'host chiama il metodo `IPersist*::Load` del motore di script per inserirlo nella risorsa di archiviazione dello script, stream o contenitore delle proprietà. In caso contrario, l'host usa il metodo `IPersist*::InitNew` o [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) per creare uno script Null. Un host che gestisce uno script come testo può usare [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) per inserire il testo dello script nel motore di script, dopo la chiamata `IActiveScriptParse::InitNew`.  
  
4.  Aggiungere gli elementi denominati. Per ogni nome elemento di livello principale (ad esempio, pagine e moduli) importato nello spazio dei nomi del motore di script, l'host chiama il metodo [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) per creare una voce nello spazio dei nomi del motore. Questo passaggio non è necessario se gli elementi denominati di livello principale fanno già parte dello stato persistente dello script caricato nel passaggio 3. Un host non usa `IActiveScript::AddNamedItem` per aggiungere elementi denominati di sottolivello (ad esempio, i controlli in una pagina HTML), invece, il motore ottiene indirettamente gli elementi di sottolivello dagli elementi di livello principale tramite le interfacce `ITypeInfo` e `IDispatch` dell'host.  
  
5.  Per eseguire lo script. L'host fa sì che il motore avvii l'esecuzione dello script, impostando il flag SCRIPTSTATE_CONNECTED nel metodo [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md). Questa chiamata eseguirebbe probabilmente qualsiasi operazione di costruzione del motore di script, tra cui associazione statica, associazione a eventi (vedere sotto) ed esecuzione di codice, in modo simile a una funzione `main()` inserita nello script.  
  
6.  Ottenere informazioni sugli elementi. Ogni volta che il motore di script deve associare un simbolo a un elemento di livello principale, chiama il metodo [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), che restituisce informazioni sull'elemento specificato.  
  
7.  Associare gli eventi. Prima di avviare lo script effettivo, il motore di script si connette agli eventi di tutti gli oggetti rilevanti tramite l'interfaccia `IConnectionPoint`.  
  
8.  Chiamare proprietà e metodi. Mentre lo script è in esecuzione, il motore di script realizza riferimenti a metodi e proprietà in oggetti denominati tramite `IDispatch::Invoke` o altri meccanismi di associazione standard OLE.  
  
## <a name="windows-script-terms"></a>Termini relativi a Windows Script  
 Questo elenco contiene le definizioni dei termini di scripting usati in questo documento.  
  
|Termine|Definizione|  
|----------|----------------|  
|Oggetto codice|Istanza creata dal motore di script associata a un elemento denominato, ad esempio il modulo di una maschera in Visual Basic o una classe C++ associata a un elemento denominato. Si tratta preferibilmente di un oggetto OLE COM (Component Object Model) che supporta l'automazione OLE, pertanto l'host o altre entità non di script possono modificare l'oggetto di codice.|  
|Elemento denominato|Oggetto OLE COM (preferibilmente un oggetto che supporta l'automazione OLE) che l'host ritiene interessante per lo script. Alcuni esempi sono la pagina HTML e il browser in un Web browser, il documento e le finestre di dialogo in Microsoft Word.|  
|Script|Dati che costituiscono il programma eseguito dal motore di script. Uno script può essere qualsiasi serie di dati eseguibili contigui, tra cui parti di testo, blocchi di `pcode` o anche codici byte eseguibili specifici del computer. Un host carica lo script nel motore di script tramite una delle interfacce `IPersist*` o tramite l'interfaccia [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Motore di script|Oggetto OLE che elabora lo script. Un motore di script implementa l'interfaccia [IActiveScript](../winscript/reference/iactivescript.md) e, facoltativamente, l'interfaccia [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Host di scripting|Applicazione o programma a cui appartiene il motore di Windows Script. L'host implementa l'interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) e, facoltativamente, l'interfaccia [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md).|  
|Scriptlet|Parte di uno script che viene allegata a un oggetto tramite l'interfaccia [IActiveScriptParse](../winscript/reference/iactivescriptparse.md). La raccolta di aggregazione di scriptlet è lo script.|  
|Linguaggio di scripting|Linguaggio in cui è scritto uno script (ad esempio, VBScript) e semantica del linguaggio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Windows Script](../winscript/windows-script-interfaces.md)