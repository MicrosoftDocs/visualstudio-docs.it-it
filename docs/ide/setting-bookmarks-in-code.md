---
title: Impostazione di segnalibri nel codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bf8367b3e4f0d20db435e16f9843e6d431c068b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="setting-bookmarks-in-code"></a>Impostazione di segnalibri nel codice

È possibile utilizzare i segnalibri per contrassegnare righe nel codice in modo da poter tornare rapidamente a una posizione specifica e spostarsi da una posizione all'altra. I comandi e le icone dei segnalibri sono disponibili in due posizioni: la finestra segnalibro (**Visualizza** > **Finestra segnalibro**) e la barra degli strumenti dell'editor di testo.

## <a name="managing-bookmarks"></a>Gestione dei segnalibri

Per aggiungere un segnalibro, posizionare il cursore sulla riga che si desidera contrassegnare con un segnalibro. Fare clic sul pulsante **Attiva/Disattiva** oppure premere CTRL+K. Viene così aggiunto il segnalibro. Se si fa clic sul pulsante Attiva/Disattiva (o si preme CTRL+K) di nuovo, il segnalibro viene rimosso. È inoltre possibile eliminare i segnalibri facendo clic sul pulsante **Elimina** nella finestra segnalibro.

> [!IMPORTANT]
> Il segnalibro viene impostato sul numero di righe, non sul codice. Se si modifica il codice, il segnalibro viene mantenuto sul numero di riga e non si sposta con il codice.

È possibile spostarsi tra i segnalibri utilizzando i pulsanti **Segnalibro successivo** e **Segnalibro precedente** nella finestra segnalibro.

È possibile organizzare i segnalibri in cartelle virtuali facendo clic su **Nuova cartella** nella finestra segnalibro e trascinando i segnalibri selezionati nella nuova cartella.

È possibile disattivare i segnalibri (senza rimuoverli) facendo clic sul pulsante **Disattiva tutti i segnalibri** nella finestra segnalibro. È possibile riabilitarli facendo clic sullo stesso pulsante (che ora è denominato **Attiva tutti i segnalibri**).

## <a name="see-also"></a>Vedere anche

[Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)