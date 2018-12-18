---
title: 'Estensione Excel di esempio: classe ActionFilter | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6f98afa819fceb4f8b8b34d5aa268f11f7b16993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Estensione Excel di esempio: classe ActionFilter

Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e rappresenta un filtro per le azioni dei test in un elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

## <a name="simple-properties"></a>Proprietà semplici

Queste proprietà di sola lettura specificano come deve essere eseguito il filtro delle azioni dei test dal framework dei test codificati dell'interfaccia utente. Ad esempio, la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornisce il nome del filtro delle azioni. Altre proprietà ottengono il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro delle azioni, il valore <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, il nome <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> per le azioni di test che vengono filtrate da questo filtro delle azioni di test. Altre indicano se applicare un timeout con <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e se l'azione di test è <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.

## <a name="processrule-method"></a>Metodo ProcessRule

Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> specificato. Questa particolare sostituzione rimuove un'azione scelta dal mouse in una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella. Restituisce quindi `false`.

## <a name="private-methods"></a>Metodi privati

Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse. Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite nella stessa cella in Excel.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
