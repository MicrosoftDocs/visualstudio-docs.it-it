---
title: Scheda output, finestra di dialogo Opzioni messaggio | Microsoft Docs
description: Utilizzare la scheda output di opzioni messaggio per specificare quali dati del messaggio vengono visualizzati nella visualizzazione messaggi. Questo articolo descrive le impostazioni disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9cb48f061cfda78e3dec8ef515df82fdefb8193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891579"
---
# <a name="output-tab-message-options-dialog-box"></a>Scheda Output, finestra di dialogo Opzioni messaggio
Utilizzare la scheda **output** per specificare i dati di ogni messaggio da elencare nella [visualizzazione messaggi](../debugger/messages-view.md). Per visualizzare la finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **Registra messaggi** dal menu **Spy** .

 Nella scheda **output** sono disponibili le impostazioni seguenti:

 **Numeri di riga** Visualizzare i numeri di riga.

 **Livello di annidamento del messaggio** Prefisso dei messaggi annidati con un periodo per ogni livello.

 **Parametri dei messaggi non elaborati** Visualizzare i valori di **wParam** e **lParam** esadecimali.

 **Parametri dei messaggi decodificati** Visualizzare i risultati della decodifica specifica del messaggio dei valori **wParam** e **lParam** .

 **Valori restituiti non elaborati** Visualizza il valore restituito **LRESULT** esadecimale.

 **Valori restituiti decodificati** Visualizza i risultati della decodifica specifica del messaggio del valore restituito di **LRESULT** .

 **Ora di origine del messaggio** Tempo trascorso dall'avvio del sistema Windows (solo per i messaggi pubblicati).

 **Posizione del mouse del messaggio** Coordinate dello schermo del mouse al momento della pubblicazione del messaggio (solo per i messaggi pubblicati).

 **Righe massime** Limitare il numero di righe conservate nella visualizzazione messaggi attualmente selezionati.

 **Registra anche i messaggi nel file** Specificare un file di output per il log dei messaggi. Questo file di output viene scritto simultaneamente con la finestra log del messaggio.

 **Salva impostazioni come predefinite** Salvare le impostazioni precedenti per le nuove finestre del flusso di messaggi. Queste impostazioni vengono salvate quando si esce da Spy + +.