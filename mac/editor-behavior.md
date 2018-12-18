---
title: Comportamento dell'editor | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 3515dfbf3a7cf8c23178aa9df243638f955593e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="editor-behavior"></a>Comportamento dell'editor

È possibile impostare i comportamenti dell'editor in modo da consentire la formattazione del codice mentre viene scritto. Queste azioni possono essere impostate in **Visual Studio > Preferenze... > Editor di testo > Comportamento**. Di seguito vengono descritte alcune delle funzioni usate più comunemente:

![Opzioni per il comportamento dell'editor](media/source-editor-image9.png)

*  Parentesi graffe di chiusura corrispondenti possono essere aggiunte automaticamente al codice durante la creazione di nuovi metodi, classi o proprietà. Quando questa opzione è selezionata, se si digita `{`, viene automaticamente aggiunto `}`.
* La formattazione immediata del codice viene attivata all'inserimento dei caratteri, ad esempio un punto e virgola o una parentesi, in base alle preferenze di formattazione impostate.
* È anche possibile scegliere di formattare il file quando lo si salva, per scrivere il codice nel modo desiderato e lasciare che sia l'IDE a formattare il codice in base alle preferenze impostate.
* Il rientro può essere impostato su Nessuno, Rientro automatico o Rientro intelligente. Di seguito vengono descritte queste impostazioni:
 * Nessuno: imposta il cursore all'inizio della riga successiva
 * Rientro automatico: imposta il cursore sulla stessa colonna nella riga successiva
 * Rientro intelligente: posiziona il rientro nella riga seguente in base al codice
* Il comportamento relativo all'interruzione delle parole differisce a seconda del sistema operativo e ai fini dello spostamento, l'editor di testo deve essere in grado di riconoscere l'inizio o la fine delle parole. La formattazione può essere impostata su Unix o Windows.

È anche possibile impostare regole di formattazione per XML, CSS, HTML e JSON.