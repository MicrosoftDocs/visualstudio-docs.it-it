---
title: Cercare un thread nella visualizzazione thread | Microsoft Docs
description: Cercare un thread specifico nella visualizzazione thread dello strumento Spy + + usando l'ID del thread o la stringa del modulo come criterio di ricerca durante il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845061"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedura: cercare un thread nella visualizzazione thread
È possibile cercare un thread specifico nella visualizzazione thread usando l'ID del thread o la stringa del modulo come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. Nei campi della finestra di dialogo vengono visualizzati gli attributi del thread selezionato nell'albero dei thread.

### <a name="to-search-for-a-thread-in-threads-view"></a>Per cercare un thread nella visualizzazione thread

1. Disporre le finestre in modo che Spy + + e una finestra [visualizzazione thread](../debugger/threads-view.md) attivi siano visibili.

2. Dal menu **Cerca** scegliere **Trova thread**.

    Verrà visualizzata la finestra di [dialogo Ricerca thread](../debugger/thread-search-dialog-box.md) .

3. Digitare l'ID del thread o una stringa del modulo come criterio di ricerca.

4. Cancellare i campi per cui non si desidera specificare i valori.

   > [!TIP]
   > Per trovare tutti i thread di proprietà di un modulo, deselezionare la casella di testo **thread** e digitare il nome del modulo nella casella **modulo** . Quindi usare **Trova successivo** per continuare la ricerca dei thread.

5. Scegliere **verso l'alto** o **verso il basso** la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un thread corrispondente, questo viene evidenziato nella finestra di visualizzazione thread.