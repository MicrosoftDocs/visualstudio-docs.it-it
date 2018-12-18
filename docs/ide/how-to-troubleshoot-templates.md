---
title: Risolvere i problemi del modello di progetto e del caricamento dei modelli di elemento di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242d053044fa66e6eb3d506382cf7cfb5d0295
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-troubleshoot-templates"></a>Procedura: Risolvere i problemi relativi ai modelli

Se un modello non viene caricato nell'ambiente di sviluppo, sono disponibili diversi metodi per individuare il problema.

## <a name="validate-the-vstemplate-file"></a>Convalidare il file con estensione vstemplate

Se il file con estensione vstemplate di un modello non rispetta lo schema di modello di Visual Studio, è possibile che il modello non venga visualizzato nella finestra di dialogo **Nuovo progetto**.

### <a name="to-validate-the-vstemplate-file"></a>Per convalidare il file con estensione vstemplate

1. Individuare il file ZIP che contiene il modello.

1. Estrarre il file ZIP.

1. Nel menu **File** di Visual Studio scegliere **Apri** > **File**.

1. Selezionare il file con estensione vstemplate per il modello e fare clic su **Apri**.

1. Verificare che il codice XML del file con estensione vstemplate rispetti lo schema del modello. Per altre informazioni sullo schema del file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Per ottenere il supporto IntelliSense durante la creazione del file con estensione vstemplate, aggiungere un attributo `xmlns` all'elemento `VSTemplate` e assegnare all'attributo il valore http://schemas.microsoft.com/developer/vstemplate/2005.

1. Salvare e chiudere il file vstemplate.

1. Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse e selezionare **Invia a** > **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.

1. Inserire il nuovo file con estensione zip nella stessa directory del file con estensione zip precedente.

1. Eliminare i file di modello estratti e il vecchio file di modello ZIP.

## <a name="enable-diagnostic-logging"></a>Abilitare la registrazione diagnostica

È possibile abilitare la registrazione diagnostica per l'individuazione dei modelli seguendo la procedura in [Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi di individuazione dei modelli (estendibilità)](../extensibility/troubleshooting-template-discovery.md)  
[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  
[Riferimento allo schema di modello](../extensibility/visual-studio-template-schema-reference.md)