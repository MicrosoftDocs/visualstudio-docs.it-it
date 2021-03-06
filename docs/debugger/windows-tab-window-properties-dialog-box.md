---
title: Scheda Windows, finestra di dialogo Proprietà finestra | Microsoft Docs
description: Utilizzare la scheda Windows delle proprietà di Windows per visualizzare le informazioni sulle finestre correlate alla finestra selezionata. Per informazioni sulle impostazioni, vedere questo articolo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffc7f8a80e86779f2cc419f841a3b80280f39c9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896403"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Scheda Finestre, finestra di dialogo Proprietà finestra
Utilizzare la scheda **Windows** per visualizzare le informazioni sulle finestre correlate alla finestra selezionata. Per visualizzare la finestra di [dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra di [visualizzazione di Windows](../debugger/windows-view.md) . Selezionare un nodo della finestra nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 Nella scheda **Windows** sono disponibili le impostazioni seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Finestra successiva**|Handle della finestra di pari livello successiva nella stessa sequenza (ordine Z) visualizzato nella visualizzazione albero della finestra ("None" se non è presente alcuna finestra successiva). Scegliere questa voce per visualizzare le proprietà della finestra successiva.|
|**Finestra precedente**|Handle della finestra di pari livello precedente nella stessa sequenza (ordine Z) visualizzato nella visualizzazione albero della finestra ("None" se non è presente una finestra precedente). Scegliere questa voce per visualizzare le proprietà della finestra precedente.|
|**Finestra padre**|Handle della finestra padre della finestra ("None" se non è presente alcun elemento padre). Scegliere questa voce per visualizzare le proprietà della finestra padre.|
|**First Child**|Handle della prima finestra figlio della finestra, nella sequenza (ordine Z) visualizzata nella visualizzazione albero della finestra ("None" se non sono presenti finestre figlio). Scegliere questo valore per visualizzare le proprietà della prima finestra figlio.|
|**Finestra proprietaria**|Handle della finestra proprietaria di questa finestra. La finestra principale di un'applicazione è in genere costituita da finestre di dialogo modali del sistema, ad esempio "None" se non è presente alcun proprietario. Scegliere questa voce per visualizzare le proprietà della finestra proprietaria.|