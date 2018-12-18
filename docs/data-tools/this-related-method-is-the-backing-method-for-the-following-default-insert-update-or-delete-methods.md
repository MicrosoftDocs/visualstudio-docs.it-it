---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 232f8622592a6abd17df4dfefddf6cf26c0c7511
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Il metodo `DataContext` selezionato viene usato attualmente come uno dei metodi di inserimento, aggiornamento o eliminazione per una delle classi di entità in Progettazione relazionale oggetti. L'eliminazione del metodo selezionato determinerà, per la classe di entità che lo stava usando, il ripristino del comportamento in fase di esecuzione predefinito per l'esecuzione dei comandi di inserimento, aggiornamento o eliminazione durante un aggiornamento.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Per eliminare il metodo selezionato e determinare l'uso degli aggiornamenti in fase di esecuzione da parte della classe di entità

- Scegliere **Sì**.

    Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Per chiudere la finestra di messaggio e lasciare invariato il metodo selezionato

- Fare clic su **No**.

    La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)