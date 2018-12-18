---
title: Installare la documentazione di Visual Studio in locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6b93d63381ba0e7afa984e6750e0dac07a8a58b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="install-and-manage-local-content"></a>Installare e gestire il contenuto locale
L'uso di Microsoft Help Viewer consente di aggiungere, rimuovere, aggiornare e spostare il contenuto della Guida installato nel computer a seconda delle esigenze di sviluppo del software.  
  
Per gestire il contenuto nel computer locale, è necessario accedere con un account che abbia autorizzazioni amministrative. È anche possibile che l'utente non possa gestire il contenuto locale se lavora in un ambiente aziendale in cui gli amministratori di sistema abbiano preso decisioni in tal senso per l'organizzazione. Per altre informazioni, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Modifica dell'origine di installazione del contenuto  
Per impostazione predefinita, Help Viewer installa il contenuto tramite un servizio online Microsoft come origine. Non è in genere necessario modificare l'origine del contenuto a meno che non si utilizzi un ambiente aziendale per cui un amministratore di sistema abbia già installato il contenuto in un'altra posizione.  
  
#### <a name="to-change-the-content-installation-source"></a>Per modificare l'origine di installazione del contenuto  
  
1.  Nella scheda **Gestisci contenuto** scegliere il pulsante di opzione **Disco**.  
  
    > [!NOTE]
    >  L'opzione **Disco** non è disponibile se l'amministratore ha impedito la modifica dell'origine dell'installazione del contenuto. Per altre informazioni, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).  
  
2.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Immettere il percorso di un file con estensione msha o l'URL di un endpoint del servizio.  
  
    -   Scegliere il pulsante Sfoglia (**…**) per trovare un file con estensione msha.  
  
    -   Nell'elenco scegliere la voce che è stata usata più di recente.  
  
## <a name="download-and-install-content-locally"></a>Scaricare e installare il contenuto localmente  
Se si installa il contenuto nel computer locale, è possibile visualizzare gli argomenti anche senza una connessione a Internet.  
  
> [!IMPORTANT]
> Per installare il contenuto, è necessario accedere con un account che disponga di autorizzazioni amministrative.  
  
> [!NOTE]
> Se l'IDE di Visual Studio è impostato su una lingua diversa dall'inglese, è possibile installare il contenuto in inglese o il contenuto localizzato oppure entrambi i contenuti. Non verrà tuttavia visualizzato alcun contenuto se si installa solo la versione inglese e la casella di controllo **Includi contenuto in inglese in tutte le schede di navigazione e nelle richieste F1** nella finestra di dialogo **Opzioni visualizzatore** è deselezionata.  
  
#### <a name="to-download-and-install-content"></a>Per scaricare e installare il contenuto  
  
1.  Scegliere la scheda **Gestisci contenuto**.  
  
2.  Nell'elenco del contenuto scegliere il collegamento **Aggiungi** accanto al libro o ai libri da scaricare e installare.  
  
     Il libro viene aggiunto all'elenco **Modifiche in sospeso** e le dimensioni stimate del libro o dei libri specificati vengono visualizzate al di sotto dell'elenco. Poiché alcuni argomenti sono presenti in più libri, le dimensioni complessive del download di più libri potrebbe essere inferiore alla somma delle dimensioni di ogni singolo libro specificato.  
  
3.  Scegliere il pulsante **Aggiorna**.  
  
     Il libro o i libri specificati vengono installati con tutti gli aggiornamenti dei libri già presenti nel computer. I tempi di installazione variano, ma è possibile visualizzare lo stato di avanzamento nella barra di stato.  
  
## <a name="removing-local-content"></a>Rimozione del contenuto locale  
È possibile risparmiare spazio su disco rimuovendo il contenuto non desiderato dal computer.  
  
> [!IMPORTANT]
> Per rimuovere il contenuto è necessario disporre di autorizzazioni amministrative.  
  
> [!NOTE]
> Non viene visualizzato alcun contenuto se l'IDE di Visual Studio viene impostato su una lingua diversa dall'inglese, se si rimuove il contenuto localizzato e se la casella di controllo **Includi contenuto in inglese in tutte le schede di navigazione e nelle richieste F1** nella finestra di dialogo **Opzioni visualizzatore** è deselezionata.  
  
#### <a name="to-remove-content"></a>Per rimuovere il contenuto  
  
1.  Scegliere la scheda **Gestisci contenuto**.  
  
2.  Nell'elenco del contenuto scegliere il collegamento **Rimuovi** accanto al libro o ai libri da rimuovere.  
  
     Il libro viene aggiunto all'elenco **Modifiche in sospeso**.  
  
3.  Scegliere il pulsante **Aggiorna**.  
  
     Il libro o i libri specificati vengono rimossi dal computer.  
  
## <a name="updating-local-content"></a>Aggiornamento del contenuto locale  
 Nella barra di stato viene indicato quando sono disponibili aggiornamenti del contenuto installato.  
  
> [!IMPORTANT]
>  Se si vuole che Help Viewer controlli automaticamente la disponibilità di aggiornamenti online, è necessario aprire la finestra di dialogo **Opzioni visualizzatore** e selezionare la casella di controllo **Connetti per verificare la disponibilità di aggiornamenti**.  
  
#### <a name="to-update-local-content"></a>Per aggiornare il contenuto locale  
  
-   Nell'angolo inferiore destro della barra di stato scegliere il collegamento **Fare clic qui per scaricare ora**.  
  
 I tempi di aggiornamento possono variare ma è possibile visualizzare lo stato di avanzamento dell'aggiornamento nella barra di stato.  
  
## <a name="moving-local-content"></a>Spostamento del contenuto locale  
 È possibile risparmiare spazio su disco spostando il contenuto installato dal computer locale in una condivisione di rete o in un'altra partizione nel computer locale.  
  
> [!IMPORTANT]
>  Per spostare il contenuto, è necessario accedere con un account che disponga di autorizzazioni amministrative.  
  
#### <a name="to-move-local-content"></a>Per spostare il contenuto locale  
  
1.  Nella scheda **Gestisci contenuto** scegliere il pulsante **Sposta** che si trova sotto **Percorso archivio locale**.  
  
     Verrà visualizzata la finestra di dialogo **Sposta contenuto**.  
  
2.  Nella casella di testo **A** immettere un percorso diverso per il contenuto e quindi scegliere **OK**.  
  
3.  Scegliere **Chiudi** dopo che il contenuto è stato spostato.  
  
## <a name="see-also"></a>Vedere anche  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)