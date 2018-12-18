---
title: Aggiornare modelli di progetti ed elementi esistenti in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9401f8a9a07f7098575ff267825982a03024e968
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-update-existing-templates"></a>Procedura: Aggiornare modelli esistenti

Dopo aver creato un modello e compresso i file in un file ZIP, può essere necessario modificare il modello. L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Uso dell'Esportazione guidata modelli per aggiornare un modello di progetto esistente

In Visual Studio è disponibile l'**Esportazione guidata modelli** che può essere usata per aggiornare un modello esistente:

1. Aprire la finestra di dialogo **Nuovo progetto** scegliendo **File** > **Nuovo** > **Progetto**.

1. Selezionare il modello da aggiornare, specificare un nome e un percorso per il progetto, quindi fare clic su **OK**.

1. Modificare il progetto in Visual Studio.

1. Nel menu **Progetto** scegliere**Esporta modello**.

    Viene aperta l'**Esportazione guidata modelli**.

1. Seguire le istruzioni della procedura guidata per esportare il modello come file con estensione zip.

1. (Facoltativo) Per aggiungere il modello alla finestra di dialogo **Nuovo progetto**, inserire il file ZIP nella directory seguente: %USERPROFILE%\Documenti\Visual Studio \<versione\>\Templates\ProjectTemplates. È necessario eseguire questo passaggio se non è stata selezionata l'opzione **Importa automaticamente il modello in Visual Studio** nell'**Esportazione guidata modelli**.

1. Eliminare il file di modello precedente con estensione zip.

## <a name="manually-updating-an-existing-template"></a>Aggiornamento manuale di un modello esistente

È possibile aggiornare un modello esistente senza usare l'**Esportazione guidata modelli** modificando i file inclusi nel file ZIP compresso.

### <a name="to-manually-update-an-existing-template"></a>Per aggiornare manualmente un modello esistente

1. Individuare il file ZIP che contiene il modello. I modelli di progetto utente in genere sono situati in %USERPROFILE%\Documenti\Visual Studio \<versione\>\Templates\ProjectTemplates.

1. Estrarre il file ZIP.

1. Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.

1. Aprire, modificare e salvare il file XML con estensione vstemplate per gestire il nuovo comportamento o i nuovi file.

    Per altre informazioni sullo schema VSTEMPLATE, vedere [Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md). Per altre informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [Parametri di modelli](../ide/template-parameters.md).

1. Selezionare i file nel modello, quindi dal menu di scelta rapida (clic destro) o dal menu a comparsa scegliere **Invia a** > **Cartella compressa**.

    I file selezionati verranno compressi in un file ZIP.

1. Inserire il nuovo file ZIP nella stessa directory del vecchio file ZIP.

1. Eliminare i file di modello estratti e il vecchio file di modello ZIP.

## <a name="see-also"></a>Vedere anche

[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  
[Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Parametri di modelli](../ide/template-parameters.md)  
[Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md)