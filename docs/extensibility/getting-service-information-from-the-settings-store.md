---
title: Recupero di informazioni di servizio dall'archivio impostazioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fdb7e95a4a4379dfbab3e56cc21e9515bb23ec0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-service-information-from-the-settings-store"></a>Acquisizione delle informazioni sul servizio dall'archivio di impostazioni
È possibile utilizzare l'archivio di impostazioni per trovare tutti i servizi disponibili o per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.  
  
### <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili  
  
1.  Creare un progetto VSIX denominato FindServicesExtension e quindi aggiungere un comando personalizzato denominato FindServicesCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In FindServicesCommand.cs, aggiungere le seguenti istruzioni using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Ottenere l'archivio di impostazioni di configurazione, quindi individuare il sottoinsieme denominato Services. Questa raccolta include tutti i servizi disponibili. Nel metodo MenuItemCommand, rimuovere il codice esistente e sostituirlo con gli elementi seguenti:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
5.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **FindServicesCommand richiamare**.  
  
     Si noterà una finestra di messaggio contenente tutti i servizi.  
  
     Per verificare queste impostazioni, è possibile utilizzare l'editor del Registro di sistema.  
  
## <a name="finding-a-specific-service"></a>Ricerca di un servizio specifico  
 È inoltre possibile utilizzare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.  
  
1.  In MenuItemCallback del progetto è stato creato nella procedura precedente, eseguire la ricerca nell'archivio di impostazioni di configurazione per il `Services` raccolta che dispone del sottoinsieme denominato dal GUID del servizio. In questo caso verrà cercato il servizio della Guida.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Compilare il progetto e avviare il debug.  
  
3.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **FindServicesCommand richiamare**.  
  
     Verrà visualizzato un messaggio con il testo **servizio Guida disponibile:** seguito da **True** o **False**. Per verificare questa impostazione, è possibile utilizzare un editor del Registro di sistema, come illustrato nei passaggi precedenti.