---
title: Pagina Debug, Creazione progetti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 305f5160ab91fdfa61e9133ab9f867194e4a117f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="debug-page-project-designer"></a>Pagina Debug, Progettazione progetti
> [!WARNING]
>  Questo argomento non si applica alle app UWP. Vedere [Avviare una sessione di debug (VB, C#, C++ e XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) in Windows Dev Center.  
  
 Usare la pagina **Debug** di **Creazione progetti** per impostare le proprietà per il comportamento di debug in un progetto Visual Basic o C#.  
  
 Per accedere alla pagina **Debug** selezionare un nodo del progetto in **Esplora soluzioni**. Nel menu **Progetto** scegliere **Proprietà** *NomeProgetto*. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Debug**.  
  
## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
 Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possibili sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**.
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. Le scelte possono includere **Qualsiasi CPU** (impostazione predefinita), **x64** e **x86**.
  
## <a name="start-action"></a>Avvia azione  
 **Avvia azione** indica l'elemento da avviare durante il debug dell'applicazione: il progetto, un programma personalizzato, un URL o nulla. Per impostazione predefinita, questa opzione è impostata su **Avvia progetto**. L'impostazione **Avvia azione** nella pagina **Debug** determina il valore della proprietà `StartAction`.  
  
 **Avvia progetto**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato il file eseguibile (per i progetti Applicazione Windows e Applicazione console). Questa opzione è selezionata per impostazione predefinita.  
  
 **Avvia programma esterno**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato un programma specifico.  
  
 **Avvia il browser con URL**  
 Scegliere questa opzione per specificare che durante il debug dell'applicazione è necessario accedere a un URL specifico.  
  
## <a name="start-options"></a>Opzioni di avvio  
 **Argomenti della riga di comando**  
 Immettere in questa casella di testo gli argomenti della riga di comando da usare per il debug.  
  
 **Directory di lavoro**  
 Immettere in questa casella di testo la directory da cui verrà avviato il progetto oppure fare clic sul pulsante Sfoglia (**...**) per scegliere una directory.  
  
 **Usa computer remoto**  
 Per il debug dell'applicazione da un computer remoto selezionare questa casella di controllo e immettere il percorso al computer remoto nella casella di testo.  
  
## <a name="enable-debuggers"></a>Abilita debugger  
 **Abilita debug codice non gestito**  
 Questa opzione specifica se è supportato il debug del codice nativo. Selezionare questa casella di controllo se si effettuano chiamate a oggetti COM o se si avvia un programma personalizzato scritto in codice nativo che chiama il progetto ed è necessario eseguire il debug del codice nativo. Deselezionare questa casella di controllo per disabilitare il debug di codice non gestito. Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Abilita debug SQL Server**  
 Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare il debug delle routine SQL dall'applicazione Visual Basic. Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Abilita processo di hosting di Visual Studio**  
 Selezionare questa casella di controllo per abilitare il processo di hosting di Visual Studio. Per impostazione predefinita, questa casella di controllo è selezionata. Per altre informazioni, vedere [Processo di hosting (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Per il debug in un'area di sicurezza è necessario abilitare questa opzione e selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** nella [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche

[Debug in Visual Studio](../../debugger/debugging-in-visual-studio.md)  
[Impostazioni di progetto per le configurazioni di debug C#](../../debugger/project-settings-for-csharp-debug-configurations.md)  
[Impostazioni di progetto per una configurazione di debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)  
[Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)  
[Procedura: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)