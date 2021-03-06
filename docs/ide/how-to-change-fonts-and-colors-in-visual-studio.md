---
title: Modificare i temi, i tipi di carattere, il testo e il contrasto per l'accessibilità
description: Informazioni su come modificare i temi colori di Visual Studio, i colori dei tipi di carattere, le dimensioni del testo e i colori a contrasto aggiuntivo per problemi di semplicità d'uso e accessibilità.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943bc9aa6efbdf5fcec038d469d39a3361315afb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875549"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Procedura: modificare i tipi di carattere, i colori e i temi in Visual Studio

È possibile modificare i tipi di carattere e i colori in Visual Studio in molti modi. Ad esempio, è possibile modificare il tema colore blu predefinito sul tema scuro (noto anche come "modalità scura"). Se questo è più adatto alle proprie esigenze, è anche possibile selezionare un tema a contrasto aggiuntivo. È possibile modificare le dimensioni predefinite del testo e del tipo di carattere nell'IDE e nell'editor di codice.

## <a name="change-the-color-theme"></a>Modificare il tema colori

Di seguito viene illustrato come modificare il tema colori del frame IDE e le finestre degli strumenti in Visual Studio.

1. Sulla barra dei menu scegliere **strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere **ambiente**  >  **generale**.

1. Nell'elenco **tema colori** scegliere il tema **blu** predefinito, il tema **chiaro** , il tema **scuro** o il tema **blu (contrasto aggiuntivo)** .

   ![Screenshot della finestra di dialogo Opzioni per modificare il tema colori](media/fonts-colors-theme.png "Screenshot della finestra di dialogo Opzioni che è possibile utilizzare per modificare il tema colori")

    > [!NOTE]
    > Quando si modifica un tema colori, il testo nell'IDE Ripristina i tipi di carattere e le dimensioni predefiniti o precedentemente personalizzati per il tema.

    :::moniker range="vs-2017"

    > [!TIP]
    > È possibile creare e modificare i temi di Visual Studio installando l' [Editor del tema colori per Visual studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor).

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > È possibile creare e modificare i temi di Visual Studio installando la [finestra di progettazione del tema colori di Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Modificare i tipi di carattere e le dimensioni del testo

È possibile modificare il tipo di carattere e la dimensione del testo per tutte le finestre degli strumenti e dei frame IDE oppure solo per determinati elementi Windows o di testo. È anche possibile modificare il tipo di carattere e la dimensione del testo nell'editor.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Per modificare il tipo di carattere e la dimensione del testo nell'IDE

1. Sulla barra dei menu scegliere **strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere   >  **tipi di carattere e colori** dell'ambiente.

1. Nell'elenco **Mostra impostazioni per** scegliere **ambiente**.

   ![Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'IDE](media/fonts-colors-environment.png "Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'IDE")

    > [!NOTE]
    > Se si intende modificare il tipo di carattere solo per le finestre degli strumenti, nell'elenco **Mostra impostazioni per** scegliere **Tutte le finestre degli strumenti di testo**.

1. Modificare le opzioni relative al **tipo di carattere** e alle **dimensioni** per modificare il tipo di carattere e la dimensione del testo per l'IDE.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Per modificare il tipo di carattere e la dimensione del testo nell'editor

1. Sulla barra dei menu scegliere **strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere   >  **tipi di carattere e colori** dell'ambiente.

1. Nell'elenco **Mostra impostazioni per** selezionare **editor di testo**.

   ![Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'editor](media/fonts-colors-text-editor.png "Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'editor")

1. Modificare le opzioni relative al **tipo di carattere** e alle **dimensioni** per modificare il tipo di carattere e la dimensione del testo per l'editor.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

Per ulteriori informazioni, vedere la pagina [modificare i tipi di carattere e i colori per la](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) pagina dell'editor.

## <a name="accessibility-options"></a>Opzioni di accessibilità

Se si verificano problemi di visione bassa, sono disponibili opzioni di tema colori. È possibile usare un'opzione a contrasto elevato per *tutte* le app e l'interfaccia utente in un computer oppure un'opzione di contrasto aggiuntiva solo per Visual Studio.

### <a name="use-windows-high-contrast"></a>Usa contrasto elevato di Windows

Utilizzare una delle seguenti procedure per impostare l'opzione di contrasto elevato di Windows:

- In Windows o in qualsiasi applicazione Microsoft, premere il tasto **ALT** di sinistra + **MAIUSC** + **Stamp** .

- In Windows scegliere **Avvia**  >  **Impostazioni**  >  **accesso facilitato** a  >  **contrasto elevato**.

    > [!WARNING]
    > L'impostazione contrasto elevato di Windows influiscono su tutte le applicazioni e sull'interfaccia utente del computer.

### <a name="use-visual-studio-extra-contrast"></a>Usa contrasto aggiuntivo di Visual Studio

Utilizzare le procedure seguenti per impostare l'opzione di contrasto aggiuntivo di Visual Studio:

1. Nella barra dei menu di Visual Studio scegliere **strumenti**  >  **Opzioni** e quindi nell'elenco Opzioni scegliere **ambiente**  >  **generale**.

1. Nell'elenco a discesa **tema colori** scegliere il tema **blu (contrasto aggiuntivo)** , quindi scegliere **OK**.

Per ulteriori informazioni sulle altre opzioni di accessibilità di Visual Studio disponibili, vedere la pagina relativa alle [funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md) .

> [!TIP]
> Se è disponibile un'opzione di accessibilità per i colori o i tipi di carattere che si ritiene possano essere utili ma che attualmente non è disponibile in Visual Studio, è possibile segnalarli selezionando **Suggerisci una funzionalità** nella [community degli sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8). Per ulteriori informazioni su questo forum e sul relativo funzionamento, vedere la pagina [Suggerisci una funzionalità](../ide/suggest-a-feature.md) .

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni su tutti gli elementi dell'interfaccia utente per i quali è possibile modificare le combinazioni di tipi di carattere e colori, vedere la pagina tipi di carattere [e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) .

## <a name="see-also"></a>Vedi anche

- [Procedura: modificare i tipi di carattere e i colori per l'editor in Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Funzionalità dell'editor di codice di Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personalizzare l'IDE di Visual Studio e l'editor](../ide/quickstart-personalize-the-ide.md)
