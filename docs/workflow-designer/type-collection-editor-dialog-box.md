---
title: La finestra di dialogo Editor raccolta di tipi | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77de1cdcffc1303a439afe743cdfd52b121779d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi

Il **Editor raccolta di tipi** la finestra di dialogo viene utilizzata per aggiungere tipi noti per il **inviare** e **ricezione** attività. Questa finestra di dialogo viene inoltre utilizzato per aggiungere argomenti di tipo generico per il **InvokeMethod** attività. Quando viene utilizzato per il **inviare** e **ricezione** attività per aggiungere tipi noti, la **Editor raccolta di tipi** la finestra di dialogo richiede le aggiunte di tipo sia univoco. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica, fare clic su **OK**, viene restituito un messaggio di errore. Quando viene utilizzato per il **InvokeMethod** attività a cui aggiungere argomenti di tipo generico, la **Editor raccolta di tipi** la finestra di dialogo consente l'aggiunta di tipi duplicati.

Per ulteriori informazioni, vedere [tipi conosciuti di contratto dati](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **raccolta di tipi** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Elenco dei tipi**|Un elenco dei tipi che sono stati aggiunti o rimossi.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive

1.  Selezionare il **inviare** o **ricezione** attività nella visualizzazione progettazione.

2.  Premere **F4** per visualizzare il **proprietà** finestra.

3.  Nel **proprietà** finestra fare clic sui puntini di sospensione accanto al **KnownTypes** proprietà.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod

1.  Selezionare il **InvokeMethod** attività nella visualizzazione progettazione.

2.  Premere **F4** per visualizzare il **proprietà** finestra.

3.  Nel **proprietà** finestra fare clic sui puntini di sospensione accanto al **GenericTypeArguments** proprietà.