---
title: 'Procedura: salvare e aprire file con codifica'
description: Informazioni su come salvare e aprire file con codifica specifica. in questo modo, quando si apre il file, Visual Studio Visualizza il file in modo corretto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d19b6f8e2e614ed397dee2e75807ded895a82d81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927912"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Procedura: salvare e aprire file con codifica

È possibile salvare i file con una codifica dei caratteri specifica per supportare le lingue bidirezionali. È anche possibile specificare una codifica all'apertura di un file, in modo che Visual Studio visualizzi il file correttamente.

## <a name="to-save-a-file-with-encoding"></a>Per salvare un file con codifica

1. Scegliere **Salva con nome** dal menu **File** e fare clic sul pulsante del menu a discesa accanto al pulsante **Salva**.

     La finestra di dialogo **Opzioni di salvataggio avanzate** viene visualizzata.

2. In **Codifica** selezionare la codifica da usare per il file.

3. Facoltativamente, in **Terminazioni riga** selezionare il formato per i caratteri di fine della riga.

     Questa opzione è utile se si prevede di scambiare il file con utenti di un altro sistema operativo.

     Se si vuole usare un file che viene codificato in un modo specifico, è possibile indicare a Visual Studio di usare tale codifica all'apertura del file. Il metodo usato dipende se il file fa parte del progetto.

> [!NOTE]
> Se si desidera salvare il file di progetto con la codifica, l'opzione **Salva file con nome** non viene abilitata fino a quando non si Scarica il progetto.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Per aprire un file codificato che fa parte di un progetto

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**.

2. Nella finestra di dialogo **Apri con** scegliere l'editor con cui aprire il file.

     Molti editor di Visual Studio, ad esempio l'editor di form, rilevano automaticamente la codifica e aprono il file in modo appropriato. Se si sceglie un editor che consente di scegliere una codifica, viene visualizzata la finestra di dialogo **Codifica**.

3. Nella finestra di dialogo **Codifica** selezionare il tipo di codifica per l'editor.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Per aprire un file codificato che non fa parte di un progetto

1. Nel menu **File** selezionare **Apri**, scegliere **File** o **File dal Web** e quindi selezionare il file da aprire.

2. Fare clic sul pulsante di menu a discesa accanto al pulsante **Apri** e scegliere **Apri con**.

3. Seguire i passaggi 2 e 3 della procedura precedente.

## <a name="see-also"></a>Vedi anche

- [Codifiche e interruzioni di riga](encodings-and-line-breaks.md)
- [Globalizzazione di Windows Form e codifica](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)
