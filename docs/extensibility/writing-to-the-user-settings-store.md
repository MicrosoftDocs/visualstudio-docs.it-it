---
title: La scrittura nell'archivio impostazioni utente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="writing-to-the-user-settings-store"></a>La scrittura nell'archivio impostazioni utente
Le impostazioni utente siano scrivibili impostazioni come quelli nel **Strumenti / opzioni** finestra di dialogo, finestre delle proprietà e altre finestre di dialogo. Estensioni di Visual Studio possono utilizzarli per archiviare piccole quantità di dati. Questa procedura dettagliata viene illustrato come aggiungere il blocco note di Visual Studio come uno strumento esterno dalla lettura e scrittura nell'archivio impostazioni utente.  
  
### <a name="backing-up-your-user-settings"></a>Backup delle impostazioni utente  
  
1.  È necessario essere in grado di reimpostare le impostazioni di strumenti esterni in modo che sia possibile eseguire il debug e ripetere la procedura. A tale scopo, è necessario salvare le impostazioni originali in modo che sia possibile ripristinarli in base alle esigenze.  
  
2.  Aprire Regedit.exe.  
  
3.  Passare a strumenti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Assicurarsi che si sta esaminando la chiave contenente \14.0Exp\ e non \14.0\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni utente vengono nell'hive del Registro di sistema "14.0Exp".  
  
4.  Pulsante destro del mouse sulla sottochiave \External Tools\ e quindi fare clic su **esportare**. Assicurarsi che **rami selezionati** è selezionata.  
  
5.  Salvare il file esterno Tools.reg risulta.  
  
6.  In un secondo momento, quando si desidera ripristinare le impostazioni di strumenti esterni, selezionare la chiave del Registro di sistema Tools \ HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External e fare clic su **eliminare** nel menu di scelta rapida.  
  
7.  Quando il **conferma eliminazione chiave** viene visualizzata la finestra di dialogo, fare clic su **Sì**.  
  
8.  Il file esterno Tools.reg salvato in precedenza, fare clic su **Apri con**, quindi fare clic su **Editor del Registro di sistema**.  
  
## <a name="writing-to-the-user-settings-store"></a>La scrittura nell'archivio impostazioni utente  
  
1.  Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In UserSettingsStoreCommand.cs, aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback, eliminare il corpo del metodo e ottenere l'utente archiviano le impostazioni, come indicato di seguito:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Ora sapere se il blocco note è già impostato come uno strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione ToolCmd è "Notepad", come indicato di seguito:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  Se il blocco note non è stato impostato come uno strumento esterno, impostarlo come indicato di seguito:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  Testare il codice. Tenere presente che aggiunge il blocco note come uno strumento esterno, pertanto è necessario ripristinare il Registro di sistema prima dell'esecuzione di una seconda volta.  
  
7.  Compilare il codice e avviare il debug.  
  
8.  Nel **strumenti** menu, fare clic su **UserSettingsStoreCommand richiamare**. Verrà aggiunto il blocco note per il **strumenti** menu.  
  
9. Ora è necessario visualizzare il blocco note gli strumenti / opzioni di menu e scegliendo **blocco note** deve utilizzare un'istanza del blocco note.