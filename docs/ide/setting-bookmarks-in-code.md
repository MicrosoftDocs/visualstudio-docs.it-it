---
title: Impostare segnalibri nel codice in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2c51b360a8df39abfd38e3da175de65c38d59bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-bookmarks-in-code"></a>Impostare segnalibri nel codice

È possibile usare i segnalibri per contrassegnare righe nel codice in modo da poter tornare rapidamente a una posizione specifica o spostarsi da una posizione all'altra. I comandi e le icone dei segnalibri sono disponibili in due posizioni: la **finestra Segnalibri** (**Visualizza** > **Finestra Segnalibri**) e la barra degli strumenti dell'editor di testo.

![Barra degli strumenti segnalibro](media/bookmark-toolbar.png)

![Finestra Segnalibri](media/bookmark-window.png)

## <a name="manage-bookmarks"></a>Gestire i segnalibri

Per aggiungere un segnalibro, posizionare il cursore sulla riga che si desidera contrassegnare con un segnalibro. Scegliere il pulsante **Attiva/Disattiva segnalibro** oppure premere **CTRL**+**K**, **CTRL**+**K**. Viene così aggiunto il segnalibro. Se si sceglie di nuovo il pulsante **Attiva/Disattiva segnalibro** (o si preme **CTRL**+**K**, **CTRL**+**K**) di nuovo, il segnalibro viene rimosso.

Per capire a colpo d'occhio a cosa si riferisce un segnalibro, è possibile rinominarlo nella **finestra Segnalibri** dal menu di scelta rapida. È possibile eliminare i segnalibri scegliendo il pulsante **Elimina** nella finestra Segnalibri.

> [!IMPORTANT]
> Il segnalibro viene impostato sul numero di righe, non sul codice. Se si modifica il codice, il segnalibro viene mantenuto sul numero di riga e non si sposta con il codice.

È possibile spostarsi tra i segnalibri usando i pulsanti **Segnalibro successivo** e **Segnalibro precedente** nella finestra Segnalibri.

È possibile organizzare i segnalibri in cartelle virtuali scegliendo **Nuova cartella** nella finestra Segnalibri e trascinando i segnalibri selezionati nella nuova cartella.

È possibile disattivare i segnalibri (senza rimuoverli) scegliendo il pulsante **Disattiva tutti i segnalibri** nella finestra Segnalibri. È possibile riabilitarli scegliendo lo stesso pulsante (che ora è denominato **Attiva tutti i segnalibri**).

## <a name="see-also"></a>Vedere anche

- [Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)