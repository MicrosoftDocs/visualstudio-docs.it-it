---
title: Organizzare i modelli in Visual Studio| Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c58bda5570be9cdb7fba7a8f90a282df7b7167a2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Procedura: Individuare e organizzare modelli di progetto e modelli di elementi

I file di modello devono essere inseriti in un percorso riconosciuto da Visual Studio per poter essere visualizzati nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**. È anche possibile creare sottocategorie personalizzate nel percorso dei modelli utente e le categorie vengono visualizzate nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**.

## <a name="locate-templates"></a>Individuare i modelli

I modelli installati e i modelli utente vengono archiviati in due percorsi diversi.

### <a name="user-templates"></a>Modelli utente

Se si aggiunge un file compresso (ZIP) che include un file vstemplate alla directory dei modelli utente, il modello viene visualizzato nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**. Per impostazione predefinita, i modelli utente si trovano in:

- %USERPROFILE%\Documenti\Visual Studio \<Versione\>\Templates\ProjectTemplates

- %USERPROFILE%\Documenti\Visual Studio \<Versione\>\Templates\ItemTemplates

Ad esempio, la directory seguente contiene i modelli di progetto personalizzati per C#:

   C:\Users\UserName\Documenti\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\

> [!TIP]
> È possibile impostare il percorso per i modelli utente in **Strumenti** > **Opzioni** > **Progetti e soluzioni** > **Percorsi**.

### <a name="installed-templates"></a>Modelli installati

Per impostazione predefinita, i modelli installati con Visual Studio si trovano in:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Linguaggio di programmazione*\\*ID impostazioni locali*

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Linguaggio di programmazione*\\*ID impostazioni locali*

Ad esempio, la directory seguente contiene i modelli di elementi di Visual Basic per la lingua inglese (LCID 1033):

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

## <a name="organize-templates"></a>Organizzare i modelli

Le categorie nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** riflettono le strutture delle directory esistenti nei percorsi dei modelli installati e dei modelli utente. È possibile organizzare i modelli utente in categorie proprie aggiungendo nuove cartelle alla directory dei modelli utente. Le finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** riflettono tutte le modifiche apportate alle categorie dei modelli.

> [!NOTE]
> Non è possibile creare una nuova categoria a livello di linguaggio di programmazione. Le nuove categorie possono essere create solo all'interno di ciascun linguaggio.

### <a name="to-create-new-user-project-template-categories"></a>Per creare nuove categorie di modelli di progetto utente

1. Creare una cartella nella cartella del linguaggio di programmazione della directory dei modelli di progetto utente. Ad esempio, per specificare una categoria **HelloWorld** per i modelli di progetti C#, creare la directory seguente:

    \%USERPROFILE%\Documenti\Visual Studio \<Versione\>\Templates\ProjectTemplates\Visual C#\HelloWorld\

1. Inserire nella nuova cartella tutti modelli di questa categoria.

1. Nel menu **File** scegliere **Nuovo** > **Progetto**.

   La categoria **HelloWorld** appare nella finestra di dialogo **Nuovo progetto**, in **Installato** > **Visual C#**.

### <a name="to-create-new-user-item-template-categories"></a>Per creare nuove categorie di modelli di elementi personalizzati

1. Creare una cartella nella cartella del linguaggio di programmazione della directory dei modelli di elementi utente. Ad esempio, per specificare una categoria **HelloWorld** per i modelli di elementi C#, creare la directory seguente:

    \%USERPROFILE%\Documenti\Visual Studio \<Versione\>\Templates\ItemTemplates\Visual C#\HelloWorld\

1. Inserire nella nuova cartella tutti modelli di questa categoria.

1. Creare un progetto oppure aprire un progetto esistente. Quindi, scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

   La categoria **HelloWorld** appare nella finestra di dialogo **Aggiungi nuovo elemento**, in **Installato** > **Elementi di Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Visualizzare i modelli in categorie padre

I modelli inclusi nelle sottocategorie possono essere visualizzati nelle relative categorie padre tramite l'elemento `NumberOfParentCategoriesToRollUp` incluso nel file con estensione vstemplate. Questa procedura è identica sia per i modelli di progetti che per i modelli di elementi.

#### <a name="to-display-templates-in-parent-categories"></a>Per visualizzare i modelli in categorie padre

1. Individuare il file ZIP che contiene il modello.

1. Estrarre il file ZIP.

1. Aprire il file vstemplate in Visual Studio.

1. Nell'elemento `TemplateData` aggiungere un elemento `NumberOfParentCategoriesToRollUp`. Ad esempio, il codice riportato di seguito rende visibile il modello nella categoria padre, ma non ai livelli superiori.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Salvare e chiudere il file vstemplate.

1. Selezionare i file nel modello, fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a** > **Cartella compressa**.

   I file verranno compressi in un file ZIP.

1. Eliminare i file di modello estratti e il vecchio file di modello ZIP.

1. Inserire il nuovo file ZIP nella stessa directory del file ZIP eliminato.

## <a name="see-also"></a>Vedere anche

[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (modelli di Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)  
[Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)
