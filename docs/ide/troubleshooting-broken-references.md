---
title: Risolvere i problemi relativi ai riferimenti interrotti | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 256e7018b29402a2d67693de3c8e2cfe18ea2f71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-broken-references"></a>Risolvere i problemi relativi ai riferimenti interrotti

Se l'applicazione tenta di usare un riferimento interrotto, viene generato un errore di eccezione. L'impossibilità di trovare il componente a cui si è fatto riferimento è la causa principale dell'errore, ma esistono diverse situazioni in cui un riferimento può essere considerato interrotto. Di seguito è riportato l'elenco delle cause di interruzione di un riferimento.

- Il percorso del riferimento del progetto non è corretto o è incompleto.

- Il file a cui viene fatto riferimento è stato eliminato.

- Il file a cui viene fatto riferimento è stato rinominato.

- Si è verificato un errore durante la connessione o l'autenticazione di rete.

- Il componente COM cui viene fatto riferimento non è installato nel computer.

Di seguito sono elencate le soluzioni a questi problemi.

> [!NOTE]
> Nel file di progetto si fa riferimento ai file contenuti negli assembly tramite percorsi assoluti. Di conseguenza, per utenti che lavorano in un ambiente con più sviluppatori è possibile che risulti mancante un assembly a cui viene fatto riferimento tramite un percorso nell'ambiente locale. Per evitare questo tipo di errori, è consigliabile, in tali casi, aggiungere riferimenti da progetto a progetto. Per altre informazioni, vedere [Programmazione con gli assembly](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Percorso di riferimento non corretto

Se i progetti sono condivisi e si trovano in computer diversi, è possibile che alcuni riferimenti non vengano individuati quando un componente viene posizionato in una directory diversa in ogni computer. I riferimenti vengono memorizzati con il nome del file del componente, ad esempio Componente. Quando si aggiunge un riferimento a un progetto, il percorso della cartella del file del componente, ad esempio C:\Componenti\,\\, viene aggiunto alla proprietà **ReferencePath** del progetto.

Quando si apre il progetto, i file dei componenti a cui viene fatto riferimento vengono cercati nelle directory del percorso dei riferimenti. Se il progetto viene aperto in un computer in cui il componente è memorizzato in una directory diversa, ad esempio D:\Componenti\\\, non sarà possibile trovare il riferimento e nell'Elenco attività verrà visualizzato un errore.

Per correggere il problema, è possibile eliminare il riferimento interrotto e sostituirlo usando la finestra di dialogo Aggiungi riferimento. Un'altra soluzione consiste nell'uso dell'elemento **ReferencePath** nelle pagine delle proprietà del progetto e nella modifica delle cartelle visualizzate nell'elenco in modo che puntino ai percorsi corretti. La proprietà **ReferencePath** viene mantenuta per ogni utente in ogni computer. Di conseguenza, la modifica del percorso dei riferimenti non ha alcun effetto sugli altri utenti del progetto.

> [!TIP]
> Nei riferimenti da progetto a progetto problemi di questo tipo non si verificano. Per questo motivo è consigliabile usare riferimenti da progetto a progetto, se possibile, anziché riferimenti a file.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Per correggere un riferimento interrotto modificando il percorso del riferimento

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

   Viene visualizzata la finestra **Creazione progetti**.

1. Se si usa Visual Basic, selezionare la pagina **Riferimenti** e fare clic sul pulsante **Percorsi riferimento**. Nella finestra di dialogo **Percorsi riferimento** digitare il percorso della cartella che contiene l'elemento a cui si vuole fare riferimento nel campo **Cartella** e quindi fare clic sul pulsante **Aggiungi cartella**.

    Se si usa C#, selezionare la pagina **Percorsi riferimento**. Nel campo **Cartella** digitare il percorso della cartella che contiene l'elemento a cui si vuole fare riferimento nel campo e quindi fare clic sul pulsante **Aggiungi cartella**.

## <a name="referenced-file-has-been-deleted"></a>File di riferimento eliminato

È possibile che il file a cui viene fatto riferimento sia stato eliminato e non sia più presente nell'unità.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Per correggere un riferimento interrotto a causa di un file che non esiste più nell'unità

- Eliminare il riferimento.

- Se il riferimento si trova in un'altra posizione all'interno del computer, leggerlo da quella posizione.

## <a name="referenced-file-has-been-renamed"></a>File di riferimento rinominato

È possibile che il file a cui viene fatto riferimento sia stato rinominato.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Per correggere un riferimento interrotto a causa della ridenominazione di un file

- Eliminare il riferimento e quindi aggiungere un riferimento al nuovo nome.

- Se il riferimento si trova in un'altra posizione all'interno del computer, è necessario leggerlo da quella posizione.

## <a name="network-connection-or-authentication-has-failed"></a>Errore durante la connessione o l'autenticazione di rete

I file possono risultare inaccessibili per molte cause, ad esempio una connessione di rete non funzionante o un'operazione di autenticazione non riuscita. Ogni causa può avere una soluzione univoca; è possibile ad esempio che sia necessario contattare il proprio amministratore locale per accedere alle risorse necessarie. Tuttavia, l'eliminazione del riferimento e la correzione del codice in cui viene usato è un'opzione sempre valida.

## <a name="com-component-is-not-installed-on-computer"></a>Componente COM non installato

Se un utente ha aggiunto un riferimento a un componente COM e un altro utente tenta di eseguire il codice in un computer nel quale tale componente non è installato, verrà generato un errore relativo all'interruzione del riferimento, che sarà possibile correggere installando il componente nel computer del secondo utente. Per altre informazioni sull'uso di riferimenti a componenti COM nei progetti, vedere [Interoperabilità COM nelle applicazioni .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Vedere anche

[Pagina Riferimenti, Creazione progetti (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
