---
title: L'associazione tardiva nelle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e205874e1c5c4e5de639e28768d6369b43c1e1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="late-binding-in-office-solutions"></a>Associazione tardiva nelle soluzioni Office
  Alcuni tipi nei modelli a oggetti delle applicazioni di Office forniscono le funzionalità disponibili tramite le funzionalità di associazione tardiva. Ad esempio, alcuni metodi e proprietà può restituire diversi tipi di oggetti a seconda del contesto dell'applicazione di Office e alcuni tipi possono esporre metodi o proprietà in contesti diversi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Progetti di Visual Basic dove **Option Strict** è disattivato e progetti Visual c# che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] può lavorare direttamente con i tipi che utilizzano queste funzionalità di associazione tardiva.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Cast implicito ed esplicito dei valori restituiti di oggetto  
 Numerosi metodi e proprietà di restituire assembly di interoperabilità primari (PIA) di Microsoft Office <xref:System.Object> valori, poiché possono restituire diversi tipi di oggetti. Ad esempio, il <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> proprietà restituisce un <xref:System.Object> perché il relativo valore restituito può essere un <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart> oggetto, a seconda del foglio attivo.  
  
 Quando una proprietà o metodo restituisce un <xref:System.Object>, è necessario convertire in modo esplicito (in Visual Basic) l'oggetto nel tipo corretto nei progetti Visual Basic in cui **Option Strict** si trova in. Non è necessario eseguire il cast esplicito <xref:System.Object> restituiscono valori nei progetti Visual Basic in cui **Option Strict** è disattivata.  
  
 Nella maggior parte dei casi, la documentazione di riferimento vengono elencati i possibili tipi di valore restituito per un membro che restituisce un <xref:System.Object>. La conversione o il cast dell'oggetto Abilita IntelliSense per l'oggetto nell'Editor di codice.  
  
 Per informazioni sulla conversione in Visual Basic, vedere [conversioni implicite ed esplicite &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [CType (funzione) &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Esempi  
 Esempio di codice riportato di seguito viene illustrato come eseguire il cast di un oggetto a un tipo specifico in un progetto di Visual Basic in cui **Option Strict** si trova in. In questo tipo di progetto, è necessario eseguire il cast esplicito di <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> proprietà per un <xref:Microsoft.Office.Interop.Excel.Range>. In questo esempio è richiesto un progetto di Excel a livello di documento con una classe foglio di lavoro denominata `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Esempio di codice riportato di seguito viene illustrato come eseguire il cast implicito un oggetto a un tipo specifico in un progetto di Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual c# che utilizza il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questi tipi di progetti, il <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> per eseguire il cast implicito proprietà una <xref:Microsoft.Office.Interop.Excel.Range>. In questo esempio è richiesto un progetto di Excel a livello di documento con una classe foglio di lavoro denominata `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="accessing-members-that-are-available-only-through-late-binding"></a>L'accesso ai membri che sono disponibili solo tramite l'associazione tardiva  
 Alcune proprietà e metodi nell'assembly di interoperabilità primari di Office sono disponibili solo tramite l'associazione tardiva. Nei progetti Visual Basic dove **Option Strict** è attiva o nei progetti Visual c# che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], è possibile utilizzare le funzionalità di associazione tardiva nelle lingue seguenti per accedere ai membri ad associazione tardiva. Nei progetti Visual Basic dove **Option Strict** è attivo, è necessario usare la reflection per accedere a questi membri.  
  
### <a name="examples"></a>Esempi  
 Esempio di codice riportato di seguito viene illustrato come accedere ai membri ad associazione tardiva in un progetto di Visual Basic in cui **Option Strict** è disattivato o in un progetto Visual c# che utilizza il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Questo esempio si accede l'associazione tardiva **nome** proprietà del **Apri File** nella finestra di dialogo di Word. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe in un progetto di Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Esempio di codice riportato di seguito viene illustrato come utilizzare la reflection per eseguire la stessa attività in un progetto di Visual Basic in cui **Option Strict** si trova in.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Utilizzo del tipo dinamico &#40;C&#35; Guida per programmatori&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  