---
title: Uso dell'archivio impostazioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3919ee3973194967f9d0367ecd13c495b3b62af2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-settings-store"></a>Uso dell'archivio di impostazioni
Esistono due tipi di archivi di impostazioni:  
  
-   Impostazioni di configurazione, sono di sola lettura delle impostazioni di Visual Studio e VSPackage. Visual Studio unisce le impostazioni da tutti i file. pkgdef noti in questo archivio.  
  
-   Impostazioni utente, che sono impostazioni scrivibile, ad esempio quelli che vengono visualizzati nelle pagine di **opzioni** la finestra di dialogo Pagine delle proprietà e altre finestre di dialogo. Estensioni di Visual Studio possono utilizzarli per l'archiviazione locale di piccole quantità di dati.  
  
 Questa procedura dettagliata viene illustrato come leggere i dati dall'archivio di impostazione di configurazione. Vedere [scrittura nell'archivio impostazioni utente](../extensibility/writing-to-the-user-settings-store.md) per una spiegazione delle modalità di scrittura nell'archivio impostazioni utente.  
  
## <a name="creating-the-example-project"></a>Creazione del progetto di esempio  
 In questa sezione viene illustrato come creare un progetto di estensione semplice con un comando di menu per la dimostrazione.  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `SettingsStoreExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Aggiungere un modello di elemento di comando personalizzato denominato **SettingsStoreCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **SettingsStoreCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Uso dell'archivio di impostazioni di configurazione  
 In questa sezione viene illustrato come rilevare e visualizzare le impostazioni di configurazione.  
  
1.  Nel file SettingsStorageCommand.cs, aggiungere le seguenti istruzioni using:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  In `MenuItemCallback`, rimuovere il corpo del metodo e aggiungere l'archivio di impostazioni di configurazione di ottenere le righe seguenti:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> è una classe helper gestito tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servizio.  
  
3.  Ora sapere se sono installati gli strumenti di Windows Phone. Il codice dovrebbe essere simile al seguente:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Testare il codice. Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **SettingsStoreCommand richiamare**.  
  
     Verrà visualizzato un messaggio **Microsoft Windows Phone Developer Tools:** seguito da **True** o **False**.  
  
 Visual Studio consente di mantenere l'archivio di impostazioni del Registro di sistema.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Per utilizzare un editor del Registro di sistema per verificare le impostazioni di configurazione  
  
1.  Aprire Regedit.exe.  
  
2.  Passare a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Assicurarsi che si sta esaminando la chiave contenente \14.0Exp_Config\ e non \14.0_Config\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione sono nell'hive del Registro di sistema "14.0Exp_Config".  
  
3.  Espandere il nodo \Installed Products\. Se il messaggio nei passaggi precedenti è **Microsoft Windows Phone Developer Tools installato: True**, quindi \Installed Products\ deve contenere un nodo di Microsoft Windows Phone Developer Tools. Se il messaggio è **Microsoft Windows Phone Developer Tools installato: False**, quindi \Installed Products\ non deve contenere un nodo di Microsoft Windows Phone Developer Tools.