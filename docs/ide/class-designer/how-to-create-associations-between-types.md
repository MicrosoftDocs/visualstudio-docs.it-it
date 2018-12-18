---
title: 'Procedura: Creare associazioni tra tipi (Progettazione classi) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d81e2f3bb671f5c88b08bf1cb26db42a6c4383a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Procedura: Creare associazioni tra tipi (Progettazione classi)
Le linee di associazione in Progettazione classi mostrano le relazioni tra le classi di un diagramma. Una linea di associazione rappresenta una classe che corrisponde al tipo di una proprietà o di un campo di un'altra classe del progetto. Le linee di associazione vengono in genere utilizzate per illustrare le relazioni più importanti tra le classi del progetto.  
  
Anche se è possibile visualizzare tutti i campi e tutte le proprietà come associazioni, è opportuno effettuare questa operazione solo per i membri importanti, a seconda degli elementi si intende evidenziare nel diagramma. I membri meno importanti possono essere visualizzati come membri normali oppure possono essere nascosti.  
  
> [!NOTE]
>  In Progettazione classi sono supportate solo le associazioni unidirezionali.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Per definire una linea di associazione in Diagramma classi  
  
1.  In Progettazione classi, nella casella degli strumenti, selezionare **Associazione**.  
  
2.  Disegnare una linea tra le due forme da collegare con un'associazione.  
  
     Nella prima classe verrà creata una nuova proprietà, visualizzata come una linea di associazione (non come una proprietà all'interno di un raggruppamento della forma) con un nome predefinito. Il tipo di questa proprietà è la forma a cui punta la linea di associazione.
  
### <a name="to-change-the-name-of-an-association"></a>Per cambiare il nome di un'associazione  
  
-   Sulla superficie del diagramma fare clic sull'etichetta della linea di associazione e modificarla.  
  
 \- oppure -  
  
1.  Fare clic sulla forma che contiene la proprietà visualizzata come associazione.  
  
     La forma otterrà lo stato attivo e i relativi membri verranno visualizzati nella finestra Dettagli classe e nella finestra Proprietà.  
  
2.  Nella finestra Dettagli classe o nella finestra Proprietà modificare il campo del nome relativo alla proprietà e premere Invio.  
  
     Il nome verrà aggiornato nella finestra **Dettagli classe**, sulla linea di associazione, nella finestra Proprietà e nel codice.  
  
## <a name="see-also"></a>Vedere anche
[Procedura: Passare dalla notazione membro alla notazione associazione](how-to-change-between-member-notation-and-association-notation.md)