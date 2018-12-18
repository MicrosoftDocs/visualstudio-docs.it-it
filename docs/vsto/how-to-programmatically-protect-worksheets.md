---
title: 'Procedura: proteggere i fogli di lavoro a livello di codice | Documenti Microsoft'
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
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 94293b90add3cbb4034278b8566ecfb1d138c09e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-worksheets"></a>Procedura: proteggere fogli di lavoro a livello di codice
  La funzionalità di protezione di Microsoft Office Excel consente di impedire la modifica degli oggetti di un foglio di lavoro da parte degli utenti o mediante codice. Per impostazione predefinita, dopo l'attivazione della protezione tutte le celle risultano bloccate.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nelle personalizzazioni a livello di documento è possibile proteggere i fogli di lavoro tramite la finestra di progettazione di Excel. È anche possibile proteggere un foglio di lavoro a livello di codice in fase di esecuzione, in qualsiasi tipo di progetto.  
  
> [!NOTE]  
>  Non è possibile aggiungere controlli Windows Form alle aree protette di un foglio di lavoro.  
  
## <a name="using-the-designer"></a>Uso della finestra di progettazione  
  
#### <a name="to-protect-a-worksheet-in-the-designer"></a>Per proteggere un foglio di lavoro nella finestra di progettazione  
  
1.  Nel **modifiche** gruppo il **revisione** scheda, fare clic su **Proteggi foglio**.  
  
     Il **Proteggi foglio** viene visualizzata la finestra di dialogo. È possibile impostare una password e specificare le azioni che gli utenti possono eseguire nel foglio di lavoro, ad esempio formattare le celle o inserire righe.  
  
 È anche possibile consentire agli utenti di modificare intervalli specifici nei fogli di lavoro protetti.  
  
#### <a name="to-allow-editing-in-specific-ranges"></a>Per consentire la modifica in intervalli specifici  
  
1.  Nel **modifiche** gruppo il **revisione** scheda, fare clic su **Consenti agli utenti la modifica degli intervalli**.  
  
     Il **Consenti agli utenti la modifica degli intervalli** viene visualizzata la finestra di dialogo. È possibile specificare gli intervalli che possono essere sbloccati mediante l'inserimento di una password e gli utenti che possono modificarli senza immettere alcuna password.  
  
## <a name="using-code-at-run-time"></a>Uso di codice in fase di esecuzione  
 Il codice seguente imposta la password tramite la variabile getPasswordFromUser, che contiene la password ottenuta dall'utente, e consente solo l'ordinamento.  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Per proteggere un foglio di lavoro mediante codice in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> del foglio di lavoro. Questo esempio presuppone l'utilizzo di un foglio di lavoro denominato `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Per proteggere un foglio di lavoro mediante codice in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> del foglio di lavoro attivo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: rimuovere la protezione dai fogli di lavoro a livello di codice](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Procedura: proteggere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Procedura: nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento Host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  