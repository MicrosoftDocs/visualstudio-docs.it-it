---
title: Filtrare e ordinare dati in un'applicazione Windows Forms | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 58117773f1f5fb973bf3ab741425d3ad7492c63f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Form
Per filtrare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà da un'espressione stringa che restituisce i record desiderati.  
  
 Per ordinare i dati, impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà sul nome di colonna per ordinare in; aggiungere `DESC` per ordinare in ordine decrescente, o aggiungere `ASC` per ordinare in ordine crescente.  
  
> [!NOTE]
>  Se l'applicazione non utilizza <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> oggetti. Per ulteriori informazioni, vedere [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati utilizzando un BindingSource (componente)  
  
-   Impostare il <xref:System.Windows.Forms.BindingSource.Filter%2A> proprietà per l'espressione da restituire. Ad esempio, il codice seguente restituisce i clienti con un `CompanyName` che inizia con "B":  
  
     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati utilizzando un BindingSource (componente)  
  
-   Impostare il <xref:System.Windows.Forms.BindingSource.Sort%2A> proprietà per la colonna che si desidera eseguire l'ordinamento. Ad esempio, il codice seguente Ordina i clienti nel `CompanyName` colonna in ordine decrescente:  
  
     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)