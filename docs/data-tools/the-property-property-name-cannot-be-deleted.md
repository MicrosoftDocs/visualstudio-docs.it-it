---
title: La proprietà non può essere eliminata
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d12f974e1949bfb96cd2d6bb774eb2b73f371689
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La proprietà \<nome proprietà > non può essere eliminato

La proprietà \<nome proprietà > non può essere eliminato perché è impostato come il **proprietà Discriminator** per l'ereditarietà tra \<nome classe > e \<nome classe >

La proprietà selezionata viene impostata come la **proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.

Impostare il **proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.

2. Impostare il **discriminatore** proprietà su una diversa proprietà.

3. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)