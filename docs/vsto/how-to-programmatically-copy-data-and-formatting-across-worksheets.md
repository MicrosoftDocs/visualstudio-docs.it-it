---
title: 'Procedura: Copiare a livello di programmazione dei dati e formattazione nei fogli di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77feefe7a2d274403e483dbaa3167f53f72ae168
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575299"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedura: Copiare a livello di programmazione dei dati e formattazione nei fogli di lavoro
  È possibile copiare dati da un intervallo di un foglio in tutti gli altri fogli in una cartella di lavoro utilizzando il <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> (metodo). Specificare un intervallo, e se si desidera copiare i dati, formattare o entrambi.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un intervallo denominato `rangeData` in un foglio di lavoro.

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: A livello di codice modificare la formattazione nelle righe del foglio di lavoro contenenti celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
