---
title: Opzioni, Editor di testo, Estensione file
description: Informazioni su come usare la pagina estensione file per specificare in che modo tutti i file con determinate estensioni di file verranno gestiti dall'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.File_Extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f163f1aca78832f38e73eaaed882ae1ac6cff17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943939"
---
# <a name="options-text-editor-file-extension"></a>Opzioni, Editor di testo, Estensione file

La finestra di dialogo Opzioni consente di specificare il modo in cui tutti i file con determinate estensioni verranno gestiti nell'ambiente di sviluppo integrato (IDE) di Visual Studio. Per ogni **estensione** è possibile selezionare uno strumento di modifica. In questo modo è possibile scegliere l'editor dell'IDE o la finestra di progettazione in cui verranno aperti i documenti di un determinato tipo. Per visualizzare queste opzioni, scegliere **Opzioni** dal **Strumenti**, espandere il nodo **Editor di testo** e selezionare **Estensione di file**.

Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento del tipo specifico viene visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica per il documento. Ciò può rivelarsi utile se si preparano versioni dei documenti di progetto da usare in piattaforme diverse o con lingue di destinazione diverse.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Estensione**

Digitare l'estensione di file di cui si vuole definire lo strumento di modifica nell'IDE.

**Editor**

Selezionare la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti con l'estensione di file specificata. Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento di questo tipo viene visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica.

**Aggiungere**

Aggiunge una voce che include l'**Estensione** e lo **Strumento di modifica** specificati all'elenco delle estensioni.

**Rimuovi**

Elimina la voce selezionata dall'elenco delle estensioni.

**Elenco estensioni**

Include tutte le estensioni per cui è stato specificato uno strumento di modifica.

**Associa file senza estensione a**

Selezionare questa opzione se si vuole specificare come devono essere gestiti nell'IDE i file senza estensione.

**Extensionless file options** (Opzioni per file senza estensione)

Visualizza lo stesso elenco di **Editor**. Selezionare la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti senza estensione di file.

## <a name="see-also"></a>Vedi anche

- [Procedura: Gestire le modalità dell'editor](../../ide/how-to-manage-editor-modes.md)
