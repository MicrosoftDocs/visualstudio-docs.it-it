---
title: Creare modelli di elementi per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd5d7fba092df5accfaad9d26cfc05f196981ba
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-create-item-templates"></a>Procedura: Creare modelli di elementi

Questo argomento spiega come creare un modello di elemento usando l'**Esportazione guidata modelli**. Se il modello è costituito da più file, vedere [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Per aggiungere un modello di elemento dell'utente alla finestra di dialogo Aggiungi nuovo elemento

1. Creare o aprire un progetto in Visual Studio.

1. Aggiungere un elemento al progetto e modificarlo, se necessario.

1. Modificare il file del codice per indicare dove verrà applicata la sostituzione dei parametri. Per altre informazioni, vedere [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).

1. Nel menu **Progetto** scegliere**Esporta modello**.

1. Nella pagina **Scegliere il tipo di modello** scegliere **Modello di elemento**, selezionare il progetto che contiene l'elemento e quindi scegliere **Avanti**.

1. Nella pagina **Selezionare elemento da esportare** scegliere l'elemento per cui si vuole creare un modello e quindi scegliere **Avanti**.

1. Nella pagina **Selezionare i riferimenti dell'elemento** selezionare i riferimenti all'assembly da includere nel modello e quindi scegliere **Avanti**.

1. Nella pagina **Selezionare le opzioni del modello** immettere il nome del modello ed eventualmente una descrizione, un'icona e un'immagine di anteprima, quindi scegliere **Fine**.

    I file per il modello vengono aggiunti a un file ZIP e copiati nella directory specificata nella procedura guidata. Il percorso predefinito è %USERPROFILE%\Documenti\Visual Studio \<versione\>\My Exported Templates.

1. Se non è stata selezionata l'opzione **Importa automaticamente il modello in Visual Studio** nell'**Esportazione guidata modelli**, individuare il modello esportato e copiarlo nella directory dei modelli di elementi dell'utente. Il percorso predefinito è %USERPROFILE%\Documenti\Visual Studio \<versione\>\Templates\ItemTemplates.

1. Chiudere e riaprire Visual Studio.

1. Creare un nuovo progetto o aprire un progetto esistente, quindi scegliere **Progetto** > **Aggiungi nuovo elemento** o premere **CTRL** + **MAIUSC** + **A**.

   Il modello di elemento appare nella finestra di dialogo **Aggiungi nuovo elemento**. Se è stata aggiunta una descrizione nell'**Esportazione guidata modelli**, la descrizione viene visualizzata sul lato destro della finestra di dialogo.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Per abilitare l'uso del modello di elemento in un progetto di app di Windows universale

La procedura guidata esegue la maggior parte delle operazioni richieste per creare un modello di base, ma in molti casi sarà necessario modificare manualmente il file VSTEMPLATE dopo aver esportato il modello. Ad esempio, se si vuole includere l'elemento nella finestra di dialogo**Aggiungi nuovo elemento** per un progetto di app di Windows universale, è necessario eseguire alcuni passaggi aggiuntivi.

1. Seguire i passaggi della sezione precedente per esportare un modello di elemento.

1. Estrarre il file ZIP creato e aprire il file VSTEMPLATE in Visual Studio.

1. Per un progetto C# di Windows universale, aggiungere il codice XML seguente all'interno dell'elemento `<TemplateData>`:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. In Visual Studio salvare e chiudere il file vstemplate.

1. Copiare e incollare il file VSTEMPLATE nel file ZIP.

     Se viene visualizzata la finestra di dialogo **Copia file**, selezionare l'opzione **Copia e sostituisci**.

È ora possibile aggiungere un elemento basato su questo modello a un progetto di Windows universale dalla finestra di dialogo **Aggiungi nuovo elemento**.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Per abilitare i modelli per sottotipi di progetto specifici

È possibile specificare che il modello deve essere visualizzato solo per determinati sottotipi di progetto, ad esempio Windows, Office, Database o Web.

1. Individuare l'elemento ProjectType nel file vstemplate per il modello di elemento.

1. Aggiungere un elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) immediatamente dopo l'elemento ProjectType.

1. Impostare il valore di testo dell'elemento su uno dei valori seguenti:

    - WINDOWS
    - Office
    - Database
    - Web

Ad esempio: `<ProjectSubType>Database</ProjectSubType>`.

L'esempio seguente illustra un modello di elemento per i progetti **Office**.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Per creare manualmente un modello di elemento senza usare l'Esportazione guidata modelli

In alcuni casi può essere utile creare manualmente un modello di elemento da zero.

1. Creare un progetto e un elemento di progetto.

1. Modificare l'elemento di progetto finché non è pronto per essere salvato come modello.

1. Modificare il file del codice per indicare dove deve avvenire la sostituzione dei parametri, se necessaria. Per altre informazioni sulla sostituzione dei parametri, vedere [Procedura: Sostituire i parametri di un modello.](../ide/how-to-substitute-parameters-in-a-template.md)

1. Creare un file XML e salvarlo con estensione VSTEMPLATE nella stessa directory del file dell'elemento del progetto.

1. Modificare il file XML VSTEMPLATE in modo da specificare i metadati del modello di elemento. Per altre informazioni, vedere [Riferimento allo schema di modello (estendibilità)](../extensibility/visual-studio-template-schema-reference.md) e l'esempio nella sezione precedente.

1. Salvare e chiudere il file vstemplate.

1. In Esplora risorse selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a** > **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.

1. Copiare il file ZIP e incollarlo nel percorso dei modelli di elemento dell'utente. In Visual Studio 2017 la directory predefinita è %USERPROFILE%\Documenti\Visual Studio 2017\Templates\ItemTemplates. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli di progetto e modelli di elementi](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche

[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  
[Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)  
[Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)
