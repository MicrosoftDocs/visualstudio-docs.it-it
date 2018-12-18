---
title: "Procedura dettagliata: Debug di un'applicazione di SharePoint tramite IntelliTrace | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 173dbc74a24166f69ca97da6d5f68332345b90ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace

Tramite IntelliTrace, è più facilmente il debug di soluzioni SharePoint. I debugger tradizionali consentono solo uno snapshot di una soluzione al momento corrente. Tuttavia, è possibile utilizzare IntelliTrace per esaminare eventi precedenti che si è verificato nella soluzione e il contesto in cui si è verificato e passare al codice.

 Questa procedura dettagliata viene illustrato come eseguire il debug di un progetto SharePoint 2010 o SharePoint 2013 in Visual Studio tramite Microsoft Monitoring Agent per raccogliere dati IntelliTrace dalle applicazioni distribuite. Per analizzare i dati, è necessario utilizzare Visual Studio Enterprise. Questo progetto include un ricevitore di funzionalità che, quando questa caratteristica è attivata, aggiunge un'attività all'elenco attività e un annuncio all'elenco di annunci. Quando questa caratteristica è disattivata, l'attività viene contrassegnata come completata e viene aggiunto un secondo annuncio all'elenco di annunci. Tuttavia, la procedura contiene un errore di logico che impedisce la corretta esecuzione del progetto. Tramite IntelliTrace, sarà di individuare e correggere l'errore.

 **Si applica a:** le informazioni contenute in questo argomento si applicano alle soluzioni di SharePoint 2010 e SharePoint 2013 che sono state create in Visual Studio.

 Questa procedura dettagliata illustra le attività seguenti:

- [Creare un ricevitore di funzionalità](#BKMK_CreateReceiver)

- [Aggiungere codice al ricevitore di funzionalità](#BKMK_AddCode)

- [Il progetto di test](#BKMK_Test1)

- [Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Eseguire il debug e correggere la soluzione di SharePoint](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Le edizioni supportate di Windows e SharePoint. Vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver"></a> Creare un ricevitore di funzionalità

Creare un progetto SharePoint vuoto che presenta un ricevitore di funzionalità.

1. Creare un progetto di soluzione SharePoint 2010 o SharePoint 2013 e denominarlo **IntelliTraceTest**.

     Il **Personalizzazione guidata SharePoint** viene visualizzata, in cui è possibile specificare sia il sito di SharePoint per il progetto e il livello di attendibilità della soluzione.

2. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante.

     IntelliTrace funziona solo in soluzioni farm.

3. In **Esplora**, aprire il menu di scelta rapida per il **funzionalità** nodo, quindi scegliere **Aggiungi funzionalità**.

     Verrà visualizzata la finestra di Feature1. feature.

4. Aprire il menu di scelta rapida per Feature1. feature e quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un modulo di codice alla funzionalità.

## <a name="BKMK_AddCode"></a> Aggiungere codice al ricevitore di funzionalità

Aggiungere quindi codice a due metodi di ricevitore di funzionalità: `FeatureActivated` e `FeatureDeactivating`. Questi metodi attivano ogni volta che una funzionalità viene attivata o disattivata in SharePoint, rispettivamente.

1. Nella parte superiore del `Feature1EventReceiver` classe, aggiungere il codice seguente, che dichiara variabili che specificano il sito di SharePoint e il sito secondario:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Sostituire il metodo `FeatureActivated` con il codice seguente:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Sostituire il metodo `FeatureDeactivating` con il codice seguente:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!"); 
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="BKMK_Test1"></a> Il progetto di test

Ora che viene aggiunto il codice al ricevitore di funzionalità e l'agente di raccolta dati è in esecuzione, distribuire ed eseguire la soluzione di SharePoint per verificare se funziona correttamente.

> [!IMPORTANT]
> Per questo esempio, viene generato un errore nel gestore eventi FeatureDeactivating. Più avanti in questa procedura dettagliata, è individuare l'errore utilizzando il file. iTrace creati dall'agente di raccolta dati.

1. Distribuire la soluzione in SharePoint e quindi aprire il sito di SharePoint in un browser.

     La funzionalità viene attivata automaticamente, causando il ricevitore di funzionalità aggiungere un annuncio e un'attività.

2. Visualizzare il contenuto degli elenchi di attività e gli annunci.

     L'elenco di annunci deve disporre di un nuovo annuncio denominato **funzionalità attivata: IntelliTraceTest_Feature1**, e l'elenco di attività deve disporre di una nuova attività denominata **Disattiva funzionalità: IntelliTraceTest_ Feature1**. Se uno di questi elementi è mancante, verificare se la funzionalità è attivata. Se non è attivata, è necessario attivarla.

3. Disattivare la funzionalità attenendosi alla procedura seguente:

    1. Nel **Azioni sito** menu in SharePoint, scegliere **Impostazioni sito**.

    2. In **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

    3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

    4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

     Il gestore dell'evento FeatureDeactivating() genera un errore.

## <a name="BKMK_CollectDiagnosticData"></a> Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent

Se si installa Microsoft Monitoring Agent nel sistema in cui è in esecuzione SharePoint, è possibile eseguire il debug delle soluzioni SharePoint utilizzando i dati che sono più specifici informazioni generiche restituite IntelliTrace. L'agente funziona all'esterno di Visual Studio utilizzando i cmdlet di PowerShell per acquisire le informazioni di debug durante l'esecuzione di soluzioni SharePoint.

> [!NOTE]
> Le informazioni di configurazione in questa sezione sono specifiche per questo esempio. Per ulteriori informazioni sulle altre opzioni di configurazione, vedere [utilizzando l'agente di raccolta autonomo IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. Nel computer in cui è in esecuzione SharePoint, [configurare Microsoft Monitoring Agent e iniziare a monitorare la soluzione](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Disattivare la funzionalità:

    1. Nel **Azioni sito** menu in SharePoint, scegliere **Impostazioni sito**.

    2. In **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

    3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

    4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

     Si verifica un errore (in questo caso, a causa l'errore generato nel gestore dell'evento FeatureDeactivating()).

3. Nella finestra di PowerShell, eseguire il [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) comando per creare il file. iTrace, arrestare il monitoraggio e riavviare la soluzione di SharePoint.

     **Stop-WebApplicationMonitoring***"\<SitoSharePoint >\\< SharePointAppName\>"* 

## <a name="BKMK_DebugSolution"></a> Eseguire il debug e correggere la soluzione di SharePoint

È ora possibile visualizzare il file di log di IntelliTrace in Visual Studio per individuare e correggere l'errore della soluzione di SharePoint.

1. Nella cartella \IntelliTraceLogs, aprire il file. iTrace in Visual Studio.

     Il **Riepilogo IntelliTrace** verrà visualizzata la pagina. Poiché l'errore non gestito, un ID di correlazione (GUID) di SharePoint viene visualizzato nell'area di un'eccezione non gestita del **Analysis** sezione. Scegliere il **Stack di chiamate** pulsante se si desidera visualizzare lo stack di chiamate in cui si è verificato l'errore.

2. Scegliere il **Debug eccezione** pulsante.

     Se richiesto, è possibile caricare i file di simboli. Nel **IntelliTrace** finestra, l'eccezione viene evidenziata come "generata: si è verificato un errore grave!".

     Nella finestra IntelliTrace, scegliere l'eccezione per visualizzare il codice che non è riuscita.

3. Correggere l'errore, aprire la soluzione di SharePoint e impostare come commento o rimuovere il **generare** istruzione all'inizio della routine FeatureDeactivating().

4. Ricompilare la soluzione in Visual Studio e quindi distribuire nuovamente in SharePoint.

5. Disattivare la funzionalità attenendosi alla procedura seguente:

    1. Nel **Azioni sito** menu in SharePoint, scegliere **Impostazioni sito**.

    2. In **Azioni sito**, scegliere il **Gestisci caratteristiche sito** collegamento.

    3. Accanto a **IntelliTraceTest Feature1**, scegliere il **disattiva** pulsante.

    4. Nella pagina di avviso, scegliere il **disattivare questa funzionalità** collegamento.

6. Aprire l'elenco di attività e verificare che il **stato** valore di un'attività disattiva "completata" e il relativo **% completato** valore equivale al 100%.

     Il codice ora viene eseguito correttamente.

## <a name="see-also"></a>Vedere anche

[Verifica e debug del codice di SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Procedura dettagliata: Verifica del codice di SharePoint tramite Unit test](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
