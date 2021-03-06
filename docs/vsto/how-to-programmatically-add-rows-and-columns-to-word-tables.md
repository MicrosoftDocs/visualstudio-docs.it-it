---
title: 'Procedura: Aggiungere righe e colonne alle tabelle di Word a livello di codice'
description: Informazioni su come usare il metodo Add dell'oggetto Rows per aggiungere righe alla tabella. È anche possibile usare il metodo Add dell'oggetto Columns per aggiungere colonne.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7cac3e11f73e53441f1bcf20c67dd5659a49a1b0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828423"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Procedura: Aggiungere righe e colonne alle tabelle di Word a livello di codice
  In una tabella di Microsoft Office Word le celle sono organizzate in righe e colonne. È possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Rows> per aggiungere righe alla tabella e il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Columns> per aggiungere colonne.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Esempi di personalizzazione a livello di documento
 Gli esempi di codice seguenti possono essere usati in una personalizzazione a livello di documento. Per usare questi esempi, eseguirli dalla classe `ThisDocument` nel progetto. Gli esempi presuppongono che il documento associato alla personalizzazione contenga già almeno una tabella.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:
>
> - Documento di Word 2013
> - Modello di Word 2013
> - Documento di Word 2010
> - Modello di Word 2010
>
>   Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Word** e quindi usare le classi di tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [Procedura: Impostare](how-to-target-office-applications-through-primary-interop-assemblies.md) come destinazione le applicazioni di Office tramite assembly di interoperabilità primari e Informazioni di riferimento sugli assembly di interoperabilità primari [di Word 2010.](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet96":::

## <a name="vsto-add-in-examples"></a>Esempi di componenti aggiuntivi VSTO
 Gli esempi di codice seguenti possono essere usati in un componente aggiuntivo VSTO. Per usare gli esempi, eseguirli dalla classe `ThisAddIn` nel progetto. Gli esempi presuppongono che il documento attivo contenga già almeno una tabella.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando modelli di componente aggiuntivo VSTO per Word.
>
> Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Word** e quindi usare le classi di tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [Procedura: Impostare](how-to-target-office-applications-through-primary-interop-assemblies.md) come destinazione le applicazioni di Office tramite assembly di interoperabilità primari e Informazioni di riferimento sugli assembly di interoperabilità primari [di Word 2010.](office-primary-interop-assemblies.md)

### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet95":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet95":::

### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.

     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet96":::
     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet96":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare tabelle di Word a livello di codice](how-to-programmatically-create-word-tables.md)
- [Procedura: Aggiungere testo e formattazione alle celle nelle tabelle di Word a livello di codice](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Procedura: Popolare a livello di codice le tabelle di Word con le proprietà del documento](how-to-programmatically-populate-word-tables-with-document-properties.md)
