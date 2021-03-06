---
title: 'Procedura: Aprire cartelle di lavoro a livello di codice'
description: Informazioni su come usare le Visual Studio per aprire a livello di codice una cartella di lavoro di Microsoft Excel o usare una cartella di lavoro esistente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824783"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: Aprire cartelle di lavoro a livello di codice
  La raccolta in Microsoft Office Excel consente di usare tutte le cartelle di lavoro aperte <xref:Microsoft.Office.Interop.Excel.Workbooks> e di aprire le cartelle di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente

1. Usare il <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo della raccolta , passando il percorso della cartella di <xref:Microsoft.Office.Interop.Excel.Workbooks> lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Una cartella di lavoro `YourWorkbook.xls` denominata deve esistere in una directory denominata `Test` nell'unità C.

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Aprire file di testo come cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Procedura: Creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: Salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
