---
title: Estensione della barra di stato | Microsoft Docs
description: Informazioni su come estendere la barra di stato di Visual Studio nella parte inferiore dell'IDE, che visualizza le informazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ab87f9c8b54d9c31466068668eb8dd5a1857a06
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070102"
---
# <a name="extend-the-status-bar"></a>Estendere la barra di stato
È possibile usare la barra di stato di Visual Studio nella parte inferiore dell'IDE per visualizzare le informazioni.

 Quando si estende la barra di stato, è possibile visualizzare informazioni e interfaccia utente in quattro aree: l'area feedback, l'indicatore di stato, l'area di animazione e l'area della finestra di progettazione. L'area commenti consente di visualizzare il testo ed evidenziare il testo visualizzato. L'indicatore di stato Mostra lo stato incrementale per le operazioni di breve durata, ad esempio il salvataggio di un file. L'area di animazione Visualizza un'animazione a ciclo continuo per le operazioni a esecuzione prolungata o per il funzionamento di lunghezza indeterminata, ad esempio la compilazione di più progetti in una soluzione. L'area della finestra di progettazione Mostra il numero di riga e di colonna della posizione del cursore.

 È possibile ottenere la barra di stato usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaccia (dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servizio). Inoltre, qualsiasi oggetto sito in una cornice di finestra può registrarsi come oggetto client della barra di stato implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaccia. Ogni volta che viene attivata una finestra, Visual Studio esegue una query sull'oggetto presente in tale finestra per l' `IVsStatusbarUser` interfaccia. Se trovato, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo sull'interfaccia restituita e l'oggetto può aggiornare la barra di stato dall'interno del metodo. Le finestre del documento, ad esempio, possono utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo per aggiornare le informazioni nell'area della finestra di progettazione quando diventano attive.

 Nelle procedure riportate di seguito si presuppone che sia stata appreso come creare un progetto VSIX e aggiungere un comando di menu personalizzato. Per informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificare la barra di stato
 Questa procedura illustra come impostare e ottenere testo, visualizzare testo statico ed evidenziare il testo visualizzato nell'area commenti e suggerimenti della barra di stato.

### <a name="read-and-write-to-the-status-bar"></a>Lettura e scrittura sulla barra di stato

1. Creare un progetto VSIX denominato **TestStatusBarExtension** e aggiungere un comando di menu denominato **TestStatusBarCommand**.

2. In *TestStatusBarCommand. cs* sostituire il metodo del gestore del comando ( `MenuItemCallback` ) con il codice seguente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Compilare il codice e avviare il debug.

4. Aprire il menu **strumenti** nell'istanza sperimentale di Visual Studio. Fare clic sul pulsante **richiama TestStatusBarCommand** .

     Si noterà che il testo nella barra di stato ora è **semplicemente scritto sulla barra di stato.** e la finestra di messaggio visualizzata ha lo stesso testo.

### <a name="update-the-progress-bar"></a>Aggiornare l'indicatore di stato

1. In questa procedura verrà illustrato come inizializzare e aggiornare l'indicatore di stato.

2. Aprire il file *TestStatusBarCommand. cs* e sostituire il `MenuItemCallback` metodo con il codice seguente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Compilare il codice e avviare il debug.

4. Aprire il menu **strumenti** nell'istanza sperimentale di Visual Studio. Fare clic sul pulsante **richiama TestStatusBarCommand** .

     Si noterà che il testo nella barra di stato ora legge la **scrittura nell'indicatore di stato.** Si noterà inoltre che l'indicatore di stato viene aggiornato ogni secondo per 20 secondi. Dopodiché la barra di stato e l'indicatore di stato vengono cancellati.

### <a name="display-an-animation"></a>Visualizzare un'animazione

1. La barra di stato Visualizza un'animazione di ciclo che indica un'operazione a esecuzione prolungata, ad esempio la compilazione di più progetti in una soluzione. Se questa animazione non è visualizzata, assicurarsi di avere le   >  impostazioni delle **Opzioni** di strumenti corrette:

     Passare alla scheda **strumenti**  >  **Opzioni**  >  **generale** e deselezionare **regola automaticamente l'esperienza visiva in base alle prestazioni del client**. Quindi selezionare l'opzione secondaria **Abilita l'esperienza visiva del rich client**. A questo punto dovrebbe essere possibile visualizzare l'animazione quando si compila il progetto nell'istanza sperimentale di Visual Studio.

     In questa procedura viene visualizzata l'animazione standard di Visual Studio che rappresenta la compilazione di un progetto o di una soluzione.

2. Aprire il file *TestStatusBarCommand. cs* e sostituire il `MenuItemCallback` metodo con il codice seguente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Compilare il codice e avviare il debug.

4. Aprire il menu **strumenti** nell'istanza sperimentale di Visual Studio e fare clic su **richiama TestStatusBarCommand**.

     Quando viene visualizzata la finestra di messaggio, dovrebbe essere visualizzata anche l'animazione nella barra di stato all'estrema destra. Quando si chiude la finestra di messaggio, l'animazione scompare.
