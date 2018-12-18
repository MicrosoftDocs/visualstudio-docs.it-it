---
title: Risoluzione dei problemi di individuazione di modello in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 72663d56844fcc34164e9408ab14c8ead234683e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello

Se si verificano problemi durante la distribuzione dei modelli di progetto o un elemento, è possibile abilitare la registrazione diagnostica.

1. Creare un file pkgdef nella cartella Common7\IDE\CommonExtensions per l'installazione (ad esempio C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) con il seguente contenuto:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Aprire un "prompt dei comandi sviluppatori" per l'installazione, cercare nella ricerca di Windows ed eseguire `devenv /updateConfiguration`.

1. Avviare Visual Studio e avviare le finestre di dialogo Nuovo progetto e nuovo elemento per inizializzare entrambi gli alberi di modello. Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Inizializzazione di struttura ogni modello aggiunge voci a questo log.

Il file di log contiene le colonne seguenti:

- **FullPathToTemplate**, che presenta i seguenti valori:

    - 1 per la distribuzione basata su manifesto

    - 0 per la distribuzione basata su disco

- **TemplateFileName**

- Altre proprietà di modello

> [!NOTE]
> Per disabilitare la registrazione, rimuovere il file pkgdef o modificare il valore di `EnableTemplateDiscoveryLog` a `dword:00000000`, quindi eseguire `devenv /updateConfiguration` nuovamente.

## <a name="see-also"></a>Vedere anche

[Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)