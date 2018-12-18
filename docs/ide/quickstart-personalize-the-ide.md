---
title: Impostare il tema colori e i tipi di carattere in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.technology:
- vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7024213ca383ee5934df1d413501065b383f7981
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Guida introduttiva: Personalizzare l'IDE e l'editor di Visual Studio

In questa guida introduttiva della durata di 5-10 minuti verranno illustrate le procedure per personalizzare il tema colori di Visual Studio e due colori del testo nell'editor di testo.

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="set-the-color-theme"></a>Impostare il tema colori

Il tema colori predefinito per Visual Studio 2017 è denominato **Blu**. Per questa esercitazione verrà cambiato in **Scuro**.

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

1. Nella pagina delle opzioni **Ambiente** > **Generale** modificare la selezione del **Tema colori** in **Scuro** e quindi scegliere **OK**.

   Verrà applicato il tema colori **Scuro** all'intero ambiente IDE.

   ![Visual Studio con tema Scuro](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> È possibile installare temi predefiniti aggiuntivi installando **Visual Studio Color Theme Editor** da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Dopo avere installato questo strumento, i temi colori aggiuntivi vengono visualizzati nell'elenco a discesa Tema colori.

## <a name="change-text-color"></a>Modificare il colore del testo

Si vedrà ora come personalizzare alcuni colori del testo per l'editor. Prima di tutto, aprire un file XML per visualizzare i colori predefiniti.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **File**.

1. Nella finestra di dialogo **Nuovo file**, nella categoria **Generale**, scegliere **File XML** e quindi scegliere **Apri**.

1. Incollare il codice XML seguente sotto la riga che contiene `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Si noti che i numeri di riga sono di colore blu-turchese e gli attributi XML di colore azzurro. Verranno di seguito modificati i colori del testo per questi elementi.

   ![Colori dei caratteri nei file XML](media/quickstart-personalize-xml-file.png)

1. Per aprire la finestra di dialogo **Opzioni**, scegliere **Strumenti** > **Opzioni** dalla barra dei menu.

1. In **Ambiente** scegliere la categoria **Tipi di carattere e colori**.

   Si noti che il testo sotto **Mostra impostazioni per** indica **Editor di testo**, ovvero l'elemento al quale si vuole applicare la modifica. Si può espandere l'elenco a discesa per visualizzare l'elenco completo delle posizioni in cui è possibile personalizzare i tipi di carattere e il colore del testo.

1. Per modificare il colore del testo dei numeri di riga, in **Elementi visualizzati** scegliere **Numero di riga**. Nella casella **Primo piano elemento** scegliere **Verde oliva**.

   ![Finestra di dialogo Opzioni, categoria Tipi di carattere e colori](media/quickstart-personalize-line-number-color.png)

   Alcuni linguaggi dispongono di impostazioni proprie per i tipi di carattere e i colori. Se ad esempio uno sviluppatore C++ desidera modificare il colore utilizzato per le funzioni, può cercare **Funzioni C++** nell'elenco **Elementi visualizzati**.

1. Prima uscire dalla finestra di dialogo, verrà modificato anche il colore degli attributi XML. Nell'elenco **Elementi visualizzati** scorrere verso il basso fino ad **Attributo XML** e selezionarlo. Nella casella **Primo piano elemento** scegliere **Verde limone**. Scegliere **OK** per salvare le selezioni e chiudere la finestra di dialogo.

   I numeri di riga sono ora di colore verde oliva e gli attributi XML di un vivace verde limone. Se si apre un altro tipo di file, ad esempio un file di codice C# o C++, si noterà che per la visualizzazione dei numeri di riga viene usato il colore verde oliva anche in questi file.

   ![File XML con i nuovi colori dei caratteri](media/quickstart-personalize-xml-file-new-colors.png)

Sono stati presentati solo un paio di modi per personalizzare i colori in Visual Studio. Per ottenere un ambiente di Visual Studio veramente su misura, è possibile esplorare tutte le altre opzioni di personalizzazione disponibili nella finestra di dialogo **Opzioni**.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Presentazione dell'IDE di Visual Studio](../ide/quickstart-ide-orientation.md)
- [Guida introduttiva: Scrittura di codice nell'editor](../ide/quickstart-editor.md)
- [Guida introduttiva: Progetti e soluzioni](../ide/quickstart-projects-solutions.md)
- [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)
- [Personalizzazione dell'editor](../ide/customizing-the-editor.md)
- [Panoramica dell'IDE di Visual Studio](../ide/visual-studio-ide.md)
