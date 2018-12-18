---
title: Sviluppo di procedura consigliate per COM, VSTO e VBA componenti aggiuntivi di Office | Documenti Microsoft
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2a1b6b9270207b3d0f8d415655231af4456e61b4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>Procedure consigliate di sviluppo di componenti aggiuntivi COM, VSTO e VBA in Office
  Se si sta sviluppando COM, componenti aggiuntivi VSTO o VBA per Office, seguire le procedure consigliate di sviluppo descritte in questo articolo.   In modo da garantire:

-  Compatibilità tra diverse versioni e le distribuzioni di Office i componenti aggiuntivi.
-  Ridotta complessità della distribuzione di componenti aggiuntivi a utenti e gli amministratori IT.
-  Non si verificano errori di runtime o l'installazione non intenzionali del componente aggiuntivo.

>Nota: L'utilizzo di [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) per preparare il computer, VSTO o VBA aggiuntivo per Windows Store non è supportato. Componenti aggiuntivi COM, VSTO e VBA non possono essere distribuiti in Office Store o di Windows Store. 
  
## <a name="do-not-check-for-office-during-installation"></a>Non verificare durante l'installazione di Office  
 Non è consigliabile che il componente aggiuntivo di rilevare se è installato Office durante il processo di installazione. Se non è installato Office, è possibile installare il componente aggiuntivo e l'utente sarà in grado di accedervi dopo l'installazione di Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Utilizzare i tipi di interoperabilità incorporati (NoPIA)  
Se la soluzione viene utilizzato .NET 4.0 o versioni successive, utilizzare tipi di interoperabilità incorporati (NoPIA) invece che a seconda di Office primario interoperabilità assembly (PIA) redistributable. Riduce le dimensioni di installazione della soluzione mediante l'incorporamento dei tipi e assicura la compatibilità futura. Office 2010 è stata l'ultima versione di Office inclusi assembly di interoperabilità primario ridistribuibile. Per ulteriori informazioni, vedere [procedura dettagliata: incorporamento delle informazioni sui tipi da assembly di Microsoft Office](https://msdn.microsoft.com/en-us/library/ee317478.aspx) e [equivalenza del tipo e i tipi di interoperabilità incorporati](/windows/uwp/porting/desktop-to-uwp-root).

Se la soluzione Usa una versione precedente di .NET, è consigliabile aggiornare la soluzione per l'utilizzo di .NET 4.0 o versione successiva. L'utilizzo di .NET 4.0 o versione successiva riduce i prerequisiti di runtime nelle versioni più recenti di Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Evitare a seconda di specifiche versioni di Office  
Se la soluzione utilizza una funzionalità disponibile solo nelle versioni più recenti di Office, verificare che la funzionalità esista (se possibile, a livello di funzionalità) in fase di esecuzione (ad esempio, utilizza la gestione o controllando la versione delle eccezioni). Convalidare le versioni minime, piuttosto che specifiche versioni, utilizzando le API supportate nel modello a oggetti, ad esempio il [Application.Version proprietà](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). Non è consigliabile basarsi su Office binaria dei metadati, percorsi di installazione o le chiavi del Registro di sistema perché questi possono variare tra le installazioni, ambienti e versioni.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Consentire l'uso di Office sia a 32 bit e a 64 bit   
La destinazione predefinita build deve supportare sia (x86) 32 bit e 64 bit (x64), a meno che la soluzione dipende dalle librerie che sono disponibili solo per un numero specifico di bit. La versione a 64 bit di Office è crescente adozione, soprattutto in ambienti di dati. Supportano sia a 32 bit e a 64 bit rende più semplice per gli utenti per la transizione tra le versioni a 32 bit e 64 bit di Office.

Quando si scrive codice VBA, safe a 64 bit di utilizzare le istruzioni declare per convertire variabili come appropriato. Inoltre, assicurarsi che i documenti possono essere condivisi tra gli utenti che eseguono versioni a 32 o 64 bit di Office fornisce codice per ogni numero di bit. Per ulteriori informazioni, vedere [a 64 bit di Visual Basic per una panoramica delle applicazioni](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Supportare ambienti con restrizioni   
La soluzione non dovrebbe richiedere i privilegi più elevati di Account utente o di amministratore. Inoltre, la soluzione non deve dipendere l'impostazione o modifica:

- Directory di lavoro corrente.
- Directory di caricamento DLL.
- La variabile PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modificare l'indirizzo dei dati condivisi e impostazioni
Se la soluzione è costituita da un componente aggiuntivo e un processo esterno a Office, non utilizzare cartella dati applicazioni dell'utente o il Registro di sistema per lo scambio di dati o le impostazioni tra il componente aggiuntivo e il processo esterno. Utilizzare invece la cartella temporanea dell'utente, la cartella documenti o la directory di installazione della soluzione.

## <a name="increment-the-version-number-with-each-update"></a>Incrementare il numero di versione con ogni aggiornamento
Impostare il numero di versione dei file binari nella soluzione e viene incrementato a ogni aggiornamento. Questo rende più semplice per gli utenti di identificare le modifiche tra le versioni e valutare la compatibilità.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornire istruzioni di supporto per le versioni più recenti di Office
I clienti richiedono ISV di fornire istruzioni di supporto per i loro COM, VSTO e VBA componenti aggiuntivi che eseguono Office. Elenca i supporto esplicito istruzioni consente ai clienti tramite Office 365 ProPlus strumenti per la conformità comprendere il supporto tecnico. 

Per fornire istruzioni di supporto per le applicazioni client di Office (ad esempio, Word o Excel), verificare innanzitutto che i componenti aggiuntivi eseguiti nella versione corrente di Office e quindi eseguire il commit per gli aggiornamenti, se il componente aggiuntivo si interrompe in una versione futura. Non è necessario testare i componenti aggiuntivi quando Microsoft rilascia una nuova compilazione o un aggiornamento a Office. Microsoft cambia raramente la piattaforma di estendibilità COM, VSTO e VBA in Office e queste modifiche verranno documentate.

>Importante: Microsoft gestisce un elenco di componenti aggiuntivi supportati per i report di conformità, le informazioni di contatto ISV. Per ottenere il componente aggiuntivo elencato, vedere [https://aka.ms/readyforwindows](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utilizzare Monitor di processo per eseguire il debug di installazione o il caricamento di problemi
Se il componente aggiuntivo presenta problemi di compatibilità durante l'installazione o di carico, potrebbe essere correlati per i problemi di accesso ai file o del Registro di sistema. Utilizzare [Process Monitor](/sysinternals/downloads/procmon) o uno strumento di debug simile per accedere e confrontare il comportamento in un ambiente di lavoro per identificare il problema.
