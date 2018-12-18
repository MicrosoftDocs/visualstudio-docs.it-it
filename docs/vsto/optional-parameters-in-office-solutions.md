---
title: Parametri facoltativi nelle soluzioni Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe40b6bc0af9df294408079c8a27dfac42df97b0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="optional-parameters-in-office-solutions"></a>Parametri facoltativi nelle soluzioni Office
  Molti dei metodi nei modelli a oggetti delle applicazioni di Microsoft Office accettano parametri facoltativi. Se si utilizza Visual Basic per sviluppare una soluzione Office in Visual Studio, non è necessario passare un valore per i parametri facoltativi. Infatti, per ogni parametro mancante vengono utilizzati automaticamente i valori predefiniti. Nella maggior parte dei casi, è anche possibile omettere i parametri facoltativi in progetti Visual c#. Tuttavia, è possibile omettere facoltativo **ref** parametri del `ThisDocument` classe nei progetti di Word a livello di documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per ulteriori informazioni sull'utilizzo dei parametri facoltativi in progetti Visual c# e Visual Basic, vedere [denominati e argomenti facoltativi &#40; C &#35; Guida per programmatori &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) e [parametri facoltativi &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  Nelle versioni precedenti di Visual Studio è necessario passare un valore per ogni parametro facoltativo nei progetti Visual C#. Per comodità, questi progetti includono una variabile globale denominata `missing` che è possibile passare a un parametro facoltativo quando si desidera utilizzare il valore predefinito del parametro. Progetti Visual c# per Office in Visual Studio includono ancora il `missing` variabile, ma è in genere non è necessario utilizzarla quando si sviluppano soluzioni Office in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], tranne quando si chiamano metodi con facoltativo **ref** parametri di `ThisDocument` classe nei progetti a livello di documento per Word.  
  
## <a name="example-in-excel"></a>Esempio in Excel  
 Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito. In questo esempio è richiesto un progetto a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Esempio in Word  
 Il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> presenta numerosi parametri facoltativi. È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Utilizzo dei parametri facoltativi di metodi nella classe ThisDocument nei progetti Visual C# a livello di documento per Word  
 Modello a oggetti di Word è disponibili numerosi metodi con facoltativo **ref** i parametri che accettano <xref:System.Object> valori. Tuttavia, è possibile omettere facoltativo **ref** i parametri dei metodi dell'oggetto generato `ThisDocument` classe nei progetti Visual c# a livello di documento per Word. Visual c# consente di omettere facoltativo **ref** parametri solo per metodi delle interfacce, non classi. Ad esempio, l'esempio di codice seguente non viene compilato, perché non è possibile omettere facoltativo **ref** parametri del <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodo la `ThisDocument` classe.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Quando si chiamano metodi della classe `ThisDocument`, attenersi le linee guida seguenti:  
  
-   Per accettare il valore predefinito facoltativo **ref** parametro, passare il `missing` variabile al parametro. La variabile `missing` viene definita automaticamente nei progetti Office di Visual C# e viene assegnata al valore <xref:System.Type.Missing> nel codice di progetto generato.  
  
-   Per specificare il valore per un parametro facoltativo **ref** parametro, dichiarare un oggetto che viene assegnato il valore che si desidera specificare e quindi passare l'oggetto al parametro.  
  
 Esempio di codice riportato di seguito viene illustrato come chiamare il <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodo specificando un valore per il *ignoreUppercase* parametro e accettando il valore predefinito per gli altri parametri.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 Se si desidera scrivere codice che omette facoltativo **ref** parametri di un metodo nel `ThisDocument` (classe), è possibile in alternativa chiamare lo stesso metodo nel <xref:Microsoft.Office.Interop.Word.Document> oggetto restituito dal <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> , proprietà e omettere il parametri da quel metodo. È possibile eseguire questa operazione perché <xref:Microsoft.Office.Interop.Word.Document> è un'interfaccia, non una classe.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 Per ulteriori informazioni sui parametri di tipo valore e riferimento, vedere [il passaggio di argomenti per valore e per riferimento &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (per Visual Basic) e [passando parametri &#40; C &#35; Guida per programmatori &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
  
  