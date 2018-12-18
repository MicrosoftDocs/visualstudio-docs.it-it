---
title: Estendere la barra di stato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a766e0c607d4d669fada794e1cf0779559f2346b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-status-bar"></a>Estendere la barra di stato
È possibile utilizzare la barra di stato di Visual Studio nella parte inferiore dell'IDE per visualizzare le informazioni.  
  
 Quando si estende la barra di stato, è possibile visualizzare informazioni e dell'interfaccia utente in quattro aree: l'area commenti e suggerimenti, l'indicatore di stato, area animazione e l'area di progettazione. L'area commenti e suggerimenti consente di visualizzare il testo ed evidenziare il testo visualizzato. L'indicatore di stato Mostra lo stato incrementale per le operazioni a esecuzione breve, ad esempio il salvataggio di un file. L'area animazione visualizza un'animazione chiuso in modo continuo per le operazioni con esecuzione prolungata o un'operazione di lunghezza indeterminata, ad esempio la creazione di più progetti in una soluzione. E l'area di progettazione Mostra il numero di riga e colonna del cursore.  
  
 È possibile ottenere la barra di stato tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaccia (dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servizio). Inoltre, qualsiasi oggetto individuato in una cornice di finestra può registrare lo stato della barra di oggetto client mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaccia. Ogni volta che viene attivata una finestra, Visual Studio l'oggetto individuato in tale finestra per una query di `IVsStatusbarUser` interfaccia. Se viene trovato, viene chiamato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo sull'interfaccia restituita e l'oggetto è possibile aggiornare la barra di stato all'interno di tale metodo. Documenti di windows, ad esempio, possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo per aggiornare le informazioni nell'area di progettazione quando diventano attivi.  
  
 Le procedure seguenti si presuppongono di aver compreso come creare un progetto VSIX e aggiungere un comando di menu personalizzato. Per informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modifica la barra di stato  
 Questa procedura viene illustrato come impostare e ottenere il testo, visualizzare testo statico ed evidenziare il testo visualizzato nell'area commenti e suggerimenti della barra di stato.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Lettura e scrittura per la barra di stato  
  
1.  Creare un progetto VSIX denominato **TestStatusBarExtension** e aggiungere un comando di menu denominato **TestStatusBarCommand**.  
  
2.  In TestStatusBarCommand.cs, sostituire il codice del metodo del gestore comando (MenuItemCallback) con le operazioni seguenti:  
  
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
  
3.  Compilare il codice e avviare il debug.  
  
4.  Aprire il **strumenti** menu nell'istanza sperimentale di Visual Studio. Fare clic su di **TestStatusBarCommand richiamare** pulsante.  
  
     Si noterà che il testo di stato barra letture ora **"Appena scritto per la barra di stato."** la finestra di messaggio visualizzato è lo stesso testo.  
  
#### <a name="updating-the-progress-bar"></a>Aggiornare l'indicatore di stato  
  
1.  In questa procedura viene illustrato come inizializzare e aggiornare l'indicatore di stato.  
  
2.  Aprire il file TestStatusBarCommand.cs e sostituire il metodo MenuItemCallback con il codice seguente:  
  
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
  
3.  Compilare il codice e avviare il debug.  
  
4.  Aprire il **strumenti** menu nell'istanza sperimentale di Visual Studio. Fare clic su **TestStatusBarCommand richiamare** pulsante.  
  
     Si noterà che il testo di stato barra letture ora **"Scrittura per l'indicatore di stato".** Verrà inoltre visualizzato l'indicatore di stato vengono aggiornati ogni secondo per 20 secondi. Dopo che la barra di stato e l'indicatore di stato vengono cancellati.  
  
#### <a name="displaying-an-animation"></a>Visualizzazione di un'animazione  
  
1.  Sulla barra di stato viene visualizzato una ciclo di animazione che indica un'operazione con esecuzione prolungata (ad esempio, la creazione di più progetti in una soluzione). Se non viene visualizzata questa animazione, accertarsi di avere il corretto **Strumenti / opzioni** impostazioni:  
  
     Passare al **Strumenti/opzioni / Generale** scheda e deselezionare **regola automaticamente in base alle prestazioni del client**. Quindi selezionare l'opzione secondaria **Abilita esperienza visiva dettagliata del client**. È ora in grado di visualizzare l'animazione quando si compila il progetto nell'istanza sperimentale di Visual Studio.  
  
     In questa procedura, viene visualizzato l'animazione di Visual Studio standard che rappresenta la creazione di un progetto o soluzione.  
  
2.  Aprire il file TestStatusBarCommand.cs e sostituire il metodo MenuItemCallback con il codice seguente:  
  
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
  
3.  Compilare il codice e avviare il debug.  
  
4.  Aprire il **strumenti** menu nell'istanza sperimentale di Visual Studio e fare clic su **TestStatusBarCommand richiamare**.  
  
     Quando viene visualizzata la finestra di messaggio, verrà inoltre visualizzato l'animazione nella barra di stato all'estrema destra. Appena si chiude la finestra di messaggio, viene rimosso l'animazione.