---
title: 'Procedura: eseguire la ricerca a livello di codice per il testo negli intervalli del foglio di lavoro | Documenti Microsoft'
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 42c95ab26437ad590d457ad926db6e070a7c8de0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Procedura: cercare testo negli intervalli dei fogli di lavoro a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> metodo il <xref:Microsoft.Office.Interop.Excel.Range> oggetto consente di cercare testo all'interno dell'intervallo. Questo testo può essere anche una delle stringhe di errore che possono essere visualizzati in una cella di foglio di lavoro, ad esempio `#NULL!` o `#VALUE!`. Per ulteriori informazioni sulle stringhe di errore, vedere [i valori delle celle errore](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nell'esempio seguente viene eseguita la ricerca di un intervallo denominato `Fruits` e modifica il tipo di carattere per le celle che contengono la parola "mele". Questa procedura viene utilizzato anche il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo che utilizza impostata in precedenza impostazioni per ripetere la ricerca di ricerca. Specificare la cella dopo il quale si desidera cercare e <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo gestisce il resto.  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> ricerca del metodo esegue il wrapping fino all'inizio dell'intervallo di ricerca quando viene raggiunta la fine dell'intervallo. Il codice deve verificare che la ricerca non ripeta in un ciclo infinito. La procedura di esempio viene illustrato come gestire questo problema mediante la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> proprietà.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [procedura: utilizzo del metodo Find in un componente aggiuntivo di Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Per cercare testo in un intervallo di foglio di lavoro  
  
1.  Dichiarare le variabili per il rilevamento dell'intero intervallo, il primo intervallo e intervallo trovato corrente.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Cercare la prima corrispondenza, specificando tutti i parametri tranne la cella per la ricerca.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Continuare la ricerca fino a quando sono presenti corrispondenze.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Confrontare il primo intervallo (`firstFind`) per **nulla**. Se `firstFind` non contiene alcun valore, i codice consente di memorizzare l'intervallo trovato (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Se l'indirizzo dell'intervallo trovato corrisponde all'indirizzo del primo intervallo trovato, uscire dal ciclo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Impostare l'aspetto dell'intervallo trovato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Eseguire un'altra ricerca.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 L'esempio seguente mostra il metodo completo.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  