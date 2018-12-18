---
title: Plug-in del controllo origine | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3395275938d78178f6f39ccd0f67dca01194bcc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo codice sorgente
La sezione di riferimento SDK plug-in controllo di origine contiene la specifica di interfaccia completa che consente ai sistemi di controllo di origine per l'integrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Specifica la sintassi e semantica tra i diversi tipi di dati e funzioni che il plug-in controllo del codice sorgente deve implementare per l'interazione con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)  
 Elenca le funzioni che devono essere implementate per il plug-in controllo del codice sorgente per garantire la conformità con l'API plug-in controllo di origine.  
  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descrive le funzioni che usa il plug-in controllo del codice sorgente per passare le informazioni dell'IDE di mentre alcuni comandi vengono eseguiti.  
  
 [Enumeratori](../extensibility/enumerators.md)  
 Elenca i tipi di dati di enumeratore nell'API di plug-in controllo di origine che è necessario conoscere il plug-in controllo del codice sorgente.  
  
 [Flag di funzionalità](../extensibility/capability-flags.md)  
 Viene descritto il `SCC_CAP_xxx` flag, che sono indicare le funzionalità di un provider di servizi.  
  
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)  
 Elenca i flag sono utili nel contesto di comandi specifici.  
  
 [Codici di errore](../extensibility/error-codes.md)  
 Vengono elencati i valori di errore comuni restituiti dalle funzioni come `SCCTRN`.  
  
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Vengono descritte le chiavi per l'accesso a Registro di sistema per individuare il controllo del codice sorgente plug-in.  
  
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Descrive un file lato client che contiene informazioni opache all'IDE, ma che viene utilizzato il plug-in controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.  
  
 [Procedure consigliate per implementare un plug-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornisce una raccolta di promemoria tecnici importante da ricordare quando si implementa l'API plug-in controllo di origine.  
  
 [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)  
 Vengono descritte le lunghezze delle stringhe utilizzate in varie funzioni limitazioni nell'API di plug-in del controllo origine.  
  
 [Glossario](../extensibility/source-control-plug-in-glossary.md)  
 Fornisce utili termini e le relative definizioni per leggere la documentazione di SDK di plug-in controllo di origine.  
  
 [Procedura: Disabilitare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Viene descritto come disabilitare gli avvisi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Esempio di plug-in del controllo di origine](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Viene fornito un esempio di plug-in controllo del codice sorgente.  
  
 [Guida per il test dei plug-in del controllo del codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descrive le procedure di test relativi a un plug-in controllo del codice sorgente.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un plug-in del controllo origine che fornisce controllo del codice sorgente quando si utilizza il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaccia di origine controllo utente (UI).  
  
 [Riferimenti su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Visualizza un elenco di argomenti di riferimento.