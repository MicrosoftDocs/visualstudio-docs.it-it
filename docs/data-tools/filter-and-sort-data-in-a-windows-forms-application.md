---
title: Filtrare e ordinare i dati in un'applicazione Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 68adaf6df9f97bee94e7cb393fa01ee133444c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648464"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrare e ordinare i dati in un'applicazione Windows Forms

Per filtrare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> su un'espressione stringa che restituisce i record desiderati.

Per ordinare i dati, impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sul nome della colonna in cui si desidera eseguire l'ordinamento. accodare `DESC` per eseguire l'ordinamento in ordine decrescente oppure accodare `ASC` per eseguire l'ordinamento in ordine crescente.

> [!NOTE]
> Se l'applicazione non utilizza <xref:System.Windows.Forms.BindingSource> componenti, è possibile filtrare e ordinare i dati utilizzando <xref:System.Data.DataView> oggetti. Per altre informazioni, vedere [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Per filtrare i dati tramite un componente BindingSource

- Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Filter%2A> sull'espressione che si desidera restituire. Il codice seguente, ad esempio, restituisce i clienti con un `CompanyName` che inizia con "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Per ordinare i dati tramite un componente BindingSource

- Impostare la proprietà <xref:System.Windows.Forms.BindingSource.Sort%2A> sulla colonna in cui si desidera eseguire l'ordinamento. Il codice seguente, ad esempio, Ordina i clienti nella colonna `CompanyName` in ordine decrescente:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)