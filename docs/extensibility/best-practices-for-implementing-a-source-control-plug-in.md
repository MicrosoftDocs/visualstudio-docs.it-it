---
title: Procedure consigliate per l'implementazione di un plug-in controllo del codice sorgente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e406bc0cd5d7e4cb082e1f5e34fa6645538d02ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedure consigliate per l'implementazione di un plug-in controllo del codice sorgente
I dettagli tecnici seguenti consentono di implementare in modo affidabile un plug-in controllo del codice sorgente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemi di gestione della memoria  
 Nella maggior parte dei casi, l'ambiente di sviluppo integrato (IDE), che rappresenta il chiamante, rilascia e alloca la memoria. Il plug-in controllo del codice sorgente restituisce stringhe e altri elementi nei buffer allocata dal chiamante. Le eccezioni sono indicate nelle descrizioni delle funzioni specifiche in cui si verificano.  
  
## <a name="arrays-of-file-names"></a>Matrici dei nomi di File  
 Quando viene passata una matrice di file, non viene passato come una matrice di nomi di file adiacenti. Viene passato come una matrice di puntatori ai nomi dei file. Ad esempio, nel [SccGet](../extensibility/sccget-function.md), vengono passati i nomi dei file per il `lpFileNames` parametro, in cui `lpFileNames` è effettivamente un puntatore a un `char **`. `lpFileNames`[0] è un puntatore al nome del primo, `lpFileNames`[1] è un puntatore al nome del secondo e così via.  
  
## <a name="large-model"></a>Modelli di grandi dimensioni  
 Tutti i puntatori sono a 32 bit, anche nei sistemi operativi a 16 bit.  
  
## <a name="fully-qualified-paths"></a>Percorsi completi  
 In cui i nomi di file o directory sono specificate come argomenti, devono essere percorsi completi o percorsi UNC, senza la barra rovesciata finale. È responsabilità del plug-in per convertire in percorsi relativi, se vale a dire un requisito del sistema di origine sottostante il controllo del codice sorgente.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Specificare il percorso completo per la DLL registrata  
 L'IDE non è più carica DLL da percorsi relativi (ad esempio,.\NewProvider.dll). (Ad esempio, C:\Providers\NewProvider.dll), è necessario specificare un percorso completo della DLL. Questo requisito aumenta la protezione dell'IDE, impedendo che il caricamento del controllo del codice sorgente non autorizzati o rappresentato DLL.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificare la presenza di un plug-in VSSCI esistente quando si installa il plug-in controllo del codice sorgente  
 Un utente che si prevede di installare il plug-in controllo del codice sorgente disponga già di un'origine controllo esistente plug-in installato nel computer. Il programma di installazione (installazione) per il plug-in che crei deve determinare se sono presenti i valori esistenti per le chiavi del Registro di sistema pertinente. Se queste chiavi sono già impostate, il programma di installazione deve chiedere all'utente se registrare il plug-in come il controllo del codice sorgente predefinito plug-in e sostituire quella che è già installato.  
  
## <a name="error-result-codes-and-reporting"></a>Codici di risultato dell'errore e creazione di report  
 Il `SCC_OK` restituito codice di una funzione di controllo di origine indica che l'operazione ha avuto esito positivo per tutti i file. Se l'operazione non riesce, è previsto per restituire l'ultimo codice di errore rilevato.  
  
 La regola per la segnalazione è che se si verifica un errore nell'IDE, è responsabile della segnalazione dell'IDE. Se si verifica un errore nel sistema di controllo di origine, il plug-in controllo del codice sorgente è responsabile per il reporting. Ad esempio, "attualmente selezionato alcun file" sarebbe stato segnalato dall'IDE, mentre "questo file è già estratto" sarebbe stato segnalato il plug-in.  
  
## <a name="the-context-structure"></a>La struttura di contesto  
 Durante la chiamata al [SccInitialize](../extensibility/sccinitialize-function.md), passa il chiamante di `ppvContext` parametro, ovvero un handle non inizializzato su un valore void. Il plug-in controllo del codice sorgente è possibile ignorare questo parametro o può allocare una struttura di qualsiasi tipo e inserire il puntatore passato un puntatore alla struttura. L'IDE non riconosce questa struttura, ma passa un puntatore alla struttura in ogni altra chiamata nel plug-in. Fornisce informazioni di cache di contesto importanti per il plug-in che è possibile utilizzare per gestire le informazioni di stato globale che persiste tra chiamate di funzione senza utilizzare le variabili globali. Il plug-in è responsabile per la struttura in una chiamata a liberare il [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Se i set di plug-in di `SCC_CAP_REENTRANT` in bit nel [SccInitialize](../extensibility/sccinitialize-function.md) (in particolare, nel `lpSccCaps` parametro), più strutture di contesto vengono utilizzate per tenere traccia di tutti i progetti aperti.  
  
## <a name="bitflags-and-other-command-options"></a>Flag di bit e altre opzioni di comando  
 Per ogni comando, ad esempio il [SccGet](../extensibility/sccget-function.md), l'IDE è possibile specificare numerose opzioni che modificano il comportamento del comando.  
  
 L'API supporta l'impostazione di determinati opzioni dall'IDE tramite il `fOptions` parametro. Queste opzioni sono descritte in [flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) con i comandi che influiscono sul. In generale, le opzioni sono per il quale non verrebbe richiesto all'utente.  
  
 Più opzioni di impostazione configurabile dall'utente non sono definite in questo modo, perché variano notevolmente tra plug-in del controllo codice sorgente. Pertanto, il metodo consigliato è un **avanzate** pulsante. Ad esempio, il **ottenere** la finestra di dialogo, l'IDE visualizza solo le informazioni che riconosce, ma viene anche visualizzato un **avanzate** se il plug-in sono disponibili opzioni per questo comando. Quando l'utente sceglie il **avanzate** pulsante, le chiamate IDE il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il controllo del codice sorgente plug-in per richiedere all'utente informazioni aggiuntive, ad esempio i flag di bit o a una data/ora. Il plug-in restituisce queste informazioni in una struttura che viene passata nuovamente durante la `SccGet` comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)