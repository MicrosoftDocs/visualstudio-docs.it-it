---
title: Riempimento automatico degli intervalli di dati a livello di codice
description: Informazioni sul modo in cui il metodo AutoFill dell'oggetto Range consente di riempire automaticamente un intervallo in un foglio di lavoro con valori.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 615331181b9402e0d2062142ad266bdd41dca4eb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824939"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Procedura: Riempire automaticamente gli intervalli con dati a modifica incrementale
  Il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo <xref:Microsoft.Office.Interop.Excel.Range> dell'oggetto consente di riempire automaticamente un intervallo in un foglio di lavoro. In genere, il metodo viene usato per archiviare valori in aumento o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> decrescente in modo incrementale in un intervallo. È possibile specificare il comportamento specificando una costante facoltativa <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> dall'enumerazione .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È necessario specificare due intervalli quando si usa <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Intervallo che chiama il metodo , che specifica il punto iniziale del riempimento <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> e contiene un valore iniziale.

- Intervallo da riempire, passato come parametro al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo . Questo intervallo di destinazione deve includere l'intervallo che contiene il valore iniziale.

    > [!NOTE]
    > Non è possibile passare <xref:Microsoft.Office.Tools.Excel.NamedRange> un controllo al posto di <xref:Microsoft.Office.Interop.Excel.Range> . Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi host e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>Compilare il codice
 La prima cella dell'intervallo da riempire deve contenere un valore iniziale.

 L'esempio richiede di riempire tre aree:

- La colonna B deve includere cinque giorni feriali. Per il valore iniziale, digitare **Monday** nella cella B1.

- La colonna C deve includere cinque mesi. Per il valore iniziale, digitare **Gennaio** nella cella C1.

- La colonna D include una serie di numeri, incrementando di due per ogni riga. Per i valori iniziali, digitare **4** nella cella D1 e **6** nella cella D2.

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Eseguire calcoli di Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
