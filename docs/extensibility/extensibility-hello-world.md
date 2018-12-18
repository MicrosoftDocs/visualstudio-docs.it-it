---
title: Hello World | Documenti Microsoft
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1b7d695f2211f01ce374ee41404d5ab49abde70a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-your-first-extension-hello-world"></a>Creare l'estensione della prima: Hello World

In questo esempio Hello World illustra creando la prima estensione per Visual Studio. In questa esercitazione Mostra come aggiungere un nuovo comando di Visual Studio.

Nel processo, si apprenderà come:

* **[Creare un progetto di estensibilità](#create-an-extensibility-project)**
* **[Aggiungere un comando personalizzato](#add-a-custom-command)**
* **[Modificare il codice sorgente](#modify-the-source-code)**
* **[Eseguirlo](#run-it)**

Per questo esempio, si userà Visual c# per aggiungere che un pulsante di menu personalizzato denominato "Say Hello World!" che è simile al seguente:

![comando di Hello world](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di aver installato il **lo sviluppo di estensioni di Visual Studio** carico di lavoro che include il modello di progetto VSIX sarà necessario e codice di esempio.

Nota: È possibile utilizzare qualsiasi versione di Visual Studio (Community, Professional o Enterprise) per creare un progetto di estensibilità di Visual Studio.

## <a name="create-an-extensibility-project"></a>Creare un progetto di estensibilità

Passaggio 1. Dal **File** menu, fare clic su **nuovo progetto**. Nella parte inferiore della schermata, è possibile immettere il nome del progetto.

Passaggio 2. Dal **modelli** menu, fare clic su **Visual c#**, fare clic su **estendibilità**e quindi fare clic su **progetto VSIX**.

![nuovo progetto](media/hello-world-new-project.png)

Viene visualizzato la pagina di introduzione e alcune risorse di esempio.

Se è necessario lasciare questa esercitazione e utilizzarla, è possibile trovare il nuovo progetto HelloWorld nel **pagina iniziale** nel **recenti** sezione.

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il manifesto, è possibile visualizzare le opzioni sono modificabili, per l'istanza, i metadati, la descrizione e versione.

Passaggio 2. Fare doppio clic su progetto (non la soluzione). Menu di scelta rapida, fare clic su **Aggiungi**, quindi fare clic su **controllo utente**.

Passaggio 3. Tornare al **estendibilità** sezione e quindi fare clic su **comando personalizzato**.

Passaggio 4. Nel **nome** campo nella parte inferiore, assegnargli un nome, ad esempio Command.cs.

![comando personalizzato](media/hello-world-custom-command.png)

Verrà elencato il nuovo comando nel **Esplora** sotto il **risorse** ramo. È anche in cui sono disponibili altri file correlati al comando, ad esempio i file PNG e ICO se si desidera modificare l'immagine.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il pulsante che si desidera aggiungere è abbastanza generico. È necessario modificare il file VSCT. CS, se si desidera apportare modifiche.

* Il file VSCT è in cui è possibile rinominare i comandi, nonché definire in cui passano nel sistema di comando di Visual Studio. Esplorare il file VSCT, si noterà la quantità di codice impostata come commento che spiega quali ogni sezione di controlli di codice.

* Il file CS è che consente di definire le azioni, ad esempio il gestore di fare clic su.

Passaggio 1. In **Esplora**, trovare il file VSCT per il nuovo comando. In questo caso, verrà chiamato CommandPackage.vsct.

![comando pacchetto vsct](media/hello-world-command-package-vsct.png)

Passaggio 2. Modifica il `ButtonText` parametro affermare "Hello World!"

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Passaggio 3. Tornare al **Esplora** e trovare il file Command.cs. Modificare la stringa `message` per il comando `string.Format(..)` su "Hello World!"

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Assicurarsi di salvare le modifiche a ogni file.

## <a name="run-it"></a>Eseguirlo

È ora possibile eseguire il codice sorgente nell'istanza sperimentale di Visual Studio.

Passaggio 1. Fare clic su **avviare** nella barra degli strumenti. Verrà compilare il progetto e avviare il debugger, avviare una nuova istanza di Visual Studio denominato il **istanza sperimentale**.

Si noterà che le parole "Istanza sperimentale" nella barra del titolo di Visual Studio.

![barra del titolo istanza sperimentale](media/hello-world-exp-instance.png)

Passaggio 2. Nel **strumenti** dal menu del **istanza sperimentale**, fare clic su **Say Hello World!**.

![risultato finale](media/hello-world-final-result.png)

Si dovrebbe vedere l'output dal nuovo comando personalizzato, in questo caso, la finestra di dialogo al centro dello schermo che consente di "Hello World!" .

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono i concetti fondamentali dell'utilizzo di estensibilità di Visual Studio, ecco dove per ulteriori informazioni:

* [Iniziare a sviluppare estensioni di Visual Studio](starting-to-develop-visual-studio-extensions.md) -esempi, esercitazioni. e la pubblicazione dell'estensione.
* [Novità di Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -nuove funzionalità di estendibilità di Visual Studio 2017
* [All'interno di Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -informazioni dettagliate di estensibilità di Visual Studio