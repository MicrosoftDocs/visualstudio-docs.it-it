---
title: 'Procedura dettagliata: Pubblicazione di un''estensione di Visual Studio | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be1402da1677388712472d4309c40ce767358f7b
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio

Questa procedura dettagliata viene illustrato come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace. Quando si aggiunge l'estensione per il Marketplace, gli sviluppatori possono utilizzare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti

 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio

In questo caso si utilizzerà l'estensione predefinita VSPackage, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in c# denominata "TestPublish" che dispone di un comando di menu. Per ulteriori informazioni, vedere [creare l'estensione della prima: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>L'estensione del pacchetto

1. Aggiornare l'estensione vsixmanifest con le informazioni corrette sul nome del prodotto, autore e versione.

  ![aggiornare l'estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in **versione** modalità. A questo punto verrà inserita come un progetto VSIX nella cartella \bin\Release l'estensione.

3. È possibile fare doppio clic per verificare l'installazione di VSIX.

## <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilare e testarlo per assicurarsi che sia installato correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio, avviare il debug. Per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, passare al **strumenti** menu e fare clic su **estensioni e aggiornamenti...** . L'estensione TestPublish dovrebbe essere visualizzato nel riquadro centrale e di essere attivata.

3. Nel **strumenti** menu, verificare che il comando di test è disponibile.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Pubblicare l'estensione di Visual Studio Marketplace

1. Assicurarsi che la versione dell'estensione di aver compilato e che sia aggiornato.

2. In un web browser, aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sito Web.

3. Nell'angolo superiore destro, fare clic su **Accedi**.

4. Usare l'account Microsoft per accedere. Se non si dispone di un account Microsoft, è possibile crearne uno a questo punto.

5. Fare clic su **pubblicare estensioni**.  Questa verrà visualizzata la pagina di gestione per tutte le estensioni.  Se non si dispone di un account del server di pubblicazione, viene chiesto di crearne uno in questo momento.

  ![Caricare in Marketplace](media/upload-to-marketplace.png)

6. Scegliere il server di pubblicazione che si desidera utilizzare per caricare l'estensione.  È possibile modificare i server di pubblicazione facendo clic sui nomi degli autori elencati a sinistra.  Fare clic su **nuova estensione** e selezionare **Visual Studio**.

7. In **1: caricare l'estensione**, è possibile scegliere di caricare un file VSIX direttamente in Visual Studio Marketplace o aggiungere un collegamento al proprio sito Web. In questo caso, si consente di caricare l'estensione, TestPublish.vsix.  Trascinare e rilasciare l'estensione o utilizzare il **fare clic su** collegamento per cercare il file.  L'estensione è reperibile nella cartella \bin\Release del progetto.  Scegliere **Continua**.

8. In **2: fornire dettagli relativi all'estensione**, alcuni campi vengono popolati automaticamente dal file vsixmanifest dall'estensione di.  Sono disponibili informazioni più dettagliate su ciascuno seguito:

    * **Nome interno** verrà utilizzato l'URL della pagina dei dettagli dell'estensione. Per un esempio, la pubblicazione di un'estensione con il nome del server di pubblicazione "myname" e specificando il nome interno per essere "myextension" comporterà un URL di "marketplace.visualstudio\.com/items?itemName=myname.myextension" per l'estensione pagina dei dettagli.
    
    * **Nome visualizzato** dell'estensione.  Ciò viene popolato automaticamente dal file vsixmanifest.
   
    * **Versione** numero dell'estensione di cui si sta caricando.  Ciò viene popolato automaticamente dal file vsixmanifest.
    
    * **ID VSIX** è l'identificatore univoco utilizzato per l'estensione Visual Studio.  È obbligatorio se si desidera avere l'estensione di essere aggiornato automaticamente.  Ciò viene popolato automaticamente dal file vsixmanifest.
    
   * **Logo** che verrà usato per l'estensione.  Questo valore sarà popolato automaticamente dal file vsixmanifest se specificato.
    
    * **Breve descrizione** delle funzionalità dell'estensione.  Questo valore sarà popolato automaticamente dal file vsixmanifest.
    
    * **Panoramica** è un ottimo strumento per includere le schermate e informazioni dettagliate sulle operazioni eseguite l'estensione.
    
    * **Le versioni di Visual Studio supportate** consente di scegliere le versioni di Visual Studio l'estensione funzionerà in.  L'estensione verrà installata solo a tali versioni.
    
    * **Edizioni di Visual Studio** consente di scegliere quali edizioni di Visual Studio in è possibile utilizzare l'estensione.  L'estensione verrà installata solo a tali versioni.
    
    * **Tipo**.  Il tipo più comune di estensioni sono **strumenti**.
    
    * **Categorie**.  Selezionare fino a tre sono migliore per l'estensione.
    
    * **Tag** sono parole chiave che consentono agli utenti di trovare l'estensione. Tag consentono di aumentare la pertinenza di ricerca delle estensioni in Marketplace.
    
    * **Prezzi categoria** è il costo dell'estensione.
    
    * **Repository di codice sorgente** consente di condividere un collegamento al codice sorgente con la community.
    
    * **Consenti a domande e risposte per l'estensione** consentirà agli utenti di lasciare domande nella pagina di voce di estensione.

9. Fare clic su **salvare e caricare**. Verrà visualizzata la pagina di gestione back per il server di pubblicazione.  L'estensione non è ancora stata pubblicata.  Per pubblicare l'estensione, fare clic sull'estensione e selezionare **Rendi pubblico**.  È possibile visualizzare come l'estensione sarà simile in Marketplace selezionando **estensione visualizzazione**.  Per i numeri di acquisizione, fare clic su **report**.  Per apportare modifiche per l'estensione, fare clic su **modifica*.

  ![Voce Menu dell'estensione](media/extension-entry-menu.png)

10. Dopo aver fatto clic **Rendi pubblico**, l'estensione è ora pubblica.  Ricerca di Visual Studio Marketplace per l'estensione.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aggiungere altri utenti per gestire l'Account del server di pubblicazione

Marketplace supporta la concessione di autorizzazioni aggiuntive agli utenti per accedere e gestire un account del server di pubblicazione.

1. Selezionare l'account del server di pubblicazione che si desidera aggiungere ulteriori utenti.

2. Selezionare **membri** e fare clic su **Aggiungi**

  ![Aggiungi utente](media/add-users.png)

3. È quindi possibile specificare l'indirizzo di posta elettronica dell'utente che si desidera aggiungere e concedere il corretto livello di accesso in **selezionare un ruolo**.  È possibile scegliere uno degli elementi seguenti:

  * **Creatore**: l'utente può pubblicare estensioni, ma non è possibile visualizzare o gestire estensioni pubblicate da altri utenti.
  
  * **Lettore**: l'utente possa visualizzare le estensioni, ma non è possibile pubblicare o gestire le estensioni.
  
  * **Collaboratore**: l'utente può pubblicare e gestire le estensioni, ma non può modificare le impostazioni di pubblicazione o gestire l'accesso.
  
  * **Proprietario**: l'utente può pubblicare e gestire le estensioni, modificare le impostazioni di pubblicazione e gestire l'accesso.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione del Marketplace di Visual Studio

Ora che viene pubblicato l'estensione, installarlo in Visual Studio e testarlo.

1. In Visual Studio, sul **strumenti** menu, fare clic su **estensioni e aggiornamenti...** .

2. Fare clic su **Online** e quindi cercare TestPublish.

3. Scegliere **Download**. L'estensione verrà quindi essere programmato per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione.

È possibile rimuovere l'estensione di Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Per rimuovere l'estensione di Visual Studio Marketplace

1. Aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sito Web.

2. Nell'angolo superiore destro, fare clic su **pubblica** estensioni.  Selezionare il server di pubblicazione utilizzato per pubblicare TestPublish.  Viene visualizzato l'elenco per TestPublish.

3. Fare doppio clic sulla voce di estensione e fare clic su **rimuovere** verrà richiesto di confermare se si desidera rimuovere l'estensione.  Fare clic su **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio, sul **strumenti** menu, fare clic su **estensione e degli aggiornamenti...** .

2. Selezionare TestPublish e quindi fare clic su **Disinstalla**. L'estensione verrà quindi pianificato per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
