---
title: Uso di Git
description: Uso di Git in Visual Studio per Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.openlocfilehash: 8b263ee21c87acd665e22d39b7eb9c46172d9548
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="working-with-git"></a>Uso di Git

Git è un sistema di controllo della versione della versione distribuito che consente ai team di lavorare contemporaneamente sugli stessi documenti. Ciò significa che è presente un server centrale che contiene tutti i file ma quando viene estratto un repository da questa origine centrale, l'intero repository viene clonato nel computer locale.

Le sezioni seguenti illustrano come è possibile usare Git per il controllo della versione in Visual Studio per Mac.

## <a name="git-version-control-menu"></a>Menu Controllo della versione di Git

L'immagine seguente illustra le opzioni offerte da Visual Studio per Mac dalla voce di menu Controllo della versione:

![Voce di menu Controllo della versione](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Push e pull 

Push e pull sono due delle azioni utilizzate più di frequente in Git. Per sincronizzare le modifiche apportate da altri utenti nel repository remoto, è necessario eseguire il **Pull** da tale posizione. Questa operazione viene eseguita in Visual Studio per Mac selezionando **Controllo della versione > Aggiorna soluzione**.

Dopo aver aggiornato i file, dopo averli rivisti e dopo averne eseguito il commit, è necessario eseguirne il **Push** nel repository remoto per consentire agli altri utenti di accedere alle modifiche apportate. Questa operazione viene eseguita in Visual Studio per Mac selezionando **Controllo della versione > Esegui push delle modifiche**. Verrà visualizzata la finestra di dialogo Push che consente di visualizzare le modifiche di cui si è eseguito il commit e di selezionare il ramo in cui eseguire il push:

![Finestra di dialogo che mostra il ramo in cui eseguire il commit](media/version-control-gitPush.png)

È anche possibile eseguire contemporaneamente il commit e il push delle modifiche, tramite la finestra di dialogo Commit:

![Opzione che mostra come eseguire commit e push contemporaneamente.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Segnala errore, Log e Unisci

Nella parte inferiore della finestra sono visualizzate cinque schede, come illustrato di seguito:

![Schede del controllo della versione](media/version-control-gitTabs.png)

Queste schede consentono le azioni seguenti:

* **Origine**: visualizza il file del codice sorgente.
* **Modifiche**: visualizza le modifiche del codice tra il file locale e il file di base. È anche possibile confrontare diverse versioni del file da hash diversi:

    ![Scheda Modifiche](media/version-control-gitChange.png)

* **Segnala errore**: visualizza il nome dell'utente associato a ogni sezione del codice.
* **Log**: visualizza tutti i commit, le ore, le date, i messaggi e gli utenti responsabili del file:

    ![Scheda Log](media/version-control-gitLog.png)

* **Unisci**: può essere usata in caso di un conflitto di unione quando si esegue il commit del lavoro. Mostra una rappresentazione visiva delle modifiche apportate dall'utente e dall'altro sviluppatore, per consentire di combinare correttamente entrambe le sezioni del codice. 

## <a name="switching-branches"></a>Cambio di rami 

Per impostazione predefinita, il primo ramo creato in un repository è denominato ramo **Master**. Tecnicamente non vi è alcuna differenza tra il ramo master e l'altro ma il ramo master viene più frequentemente considerato come ramo "attivo" o di "produzione" dai team di sviluppo.

È possibile creare una linea di sviluppo indipendente, creando una diramazione del ramo master (o di qualsiasi altro ramo). Questo offre una nuova versione del ramo master in un determinato punto nel tempo, consentendo lo sviluppo indipendente di ciò che è "attivo". Questo uso dei rami è frequente per funzionalità nell'ambiente di sviluppo.

Gli utenti possono creare tutti i rami che desiderano per ogni repository, ma è consigliabile eliminare i rami quando si finisce di usarli per mantenere organizzato il repository.

Per visualizzare i rami in Visual Studio per Mac, spostarsi su **Controllo della versione > Gestisci rami ed origini remote...**:

![Visualizzazione dei rami](media/version-control-gitBranch2.png)

Passare a un altro ramo selezionandolo nell'elenco e premendo il pulsante **Passa al ramo**.

Per creare un nuovo ramo, selezionare il pulsante **Nuovo** nella finestra di dialogo di configurazione del repository Git. Inserire il nome del nuovo ramo:

![Creare un nuovo ruolo](media/version-control-gitBranch.png)

È anche possibile impostare un ramo remoto per il proprio ramo di _verifica_. Per altre informazioni sui rami di verifica, vedere la [documentazione su Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Vedere il ramo corrente nel riquadro della soluzione, accanto al nome del progetto:

 ![Ramo corrente visualizzato nel riquadro soluzione](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Revisione e commit 

Per rivedere le modifiche nei file, usare le schede Modifiche, Segnala errore, Log e Unisci in ogni documento, come illustrato precedentemente in questo argomento.

Rivedere tutte le modifiche del progetto spostandosi sulla voce di menu **Controllo della versione > Review Solution and Commit (Rivedi soluzione ed esegui commit)**:

![Visualizzazione di revisione del codice](media/version-control-gitReviewCommit.png)

Ciò consente di visualizzare tutte le modifiche in ogni file di un progetto con l'opzione di annullarle, creare una patch o eseguire il commit.

Per eseguire il commit di un file in un repository remoto, premere **Commit...**, inserire un messaggio di commit e confermare con il pulsante Commit:

![Commit di un file](media/version-control-gitCommit.png)

Dopo aver eseguito il commit delle modifiche, eseguirne il push in un repository remoto per renderle visibili agli altri utenti.