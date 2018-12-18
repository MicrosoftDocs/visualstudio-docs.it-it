---
title: L'accesso a un'area del modulo in fase di esecuzione | Documenti Microsoft
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
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 70e9a970251aa5b95cff5983f5e2ce5e0c804a61
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="accessing-a-form-region-at-run-time"></a>Accesso a un'area del modulo in fase di esecuzione
  
  
|Si applica a|  
|----------------|  
|Le informazioni fornite in questo argomento sono valide solo per i tipi di progetto e le versioni di Microsoft Office seguenti. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo di progetto**<br /><br /> -Progetti di componente aggiuntivo VSTO<br /><br /> **Versione di Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Usare la classe `Globals` per accedere alle aree del modulo da qualsiasi punto del progetto Outlook. Per ulteriori informazioni sul `Globals` classe, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Accesso alle aree del modulo visualizzate in una specifica finestra di controllo Outlook  
 Per accedere a tutte le aree del modulo visualizzate in uno specifico controllo Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta il controllo.  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nel controllo che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  
  
## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Accesso alle aree del modulo visualizzate in una specifica finestra di esplorazione Outlook  
 Per accedere a tutte le aree del modulo visualizzate in una specifica finestra di esplorazione Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che rappresenta la finestra di esplorazione.  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nella finestra di esplorazione che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  
  
## <a name="accessing-all-form-regions"></a>Accesso a tutte le aree del modulo  
 Per accedere a tutte le aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli, chiamare la proprietà `FormRegions` della classe `Globals` .  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli. Viene quindi effettuato l'accesso a un'area del modulo denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  
  
## <a name="accessing-controls-on-a-form-region"></a>Accesso ai controlli presenti in un'area del modulo  
 Per accedere ai controlli presenti in un'area del modulo usando la classe `Globals` , è necessario rendere tali controlli accessibili al codice dall'esterno del file di codice dell'area del modulo.  
  
### <a name="form-regions-designed-in-the-form-region-designer"></a>Aree del modulo progettate nella finestra di progettazione dell'area del modulo  
 Per C# cambiare il modificatore di ogni controllo a cui si vuole accedere. Per eseguire questa operazione, selezionare ogni controllo nella finestra di progettazione dell'area del modulo e impostare la proprietà **Modificatori** su **Interna** o **pubblica** nella finestra **Proprietà** . Ad esempio, se si imposta la proprietà **Modifier** di `textBox1` su **Internal**, è possibile accedere a `textBox1` digitando `Globals.FormRegions.FormRegion1.textBox1`.  
  
 Per Visual Basic non è necessario cambiare il modificatore.  
  
### <a name="imported-form-regions"></a>Aree del modulo importate  
 Quando si importa un'area del modulo progettata in Outlook, il modificatore di accesso di ogni controllo presente nell'area del modulo diventa privato. Dal momento che non è possibile usare la finestra di progettazione dell'area del modulo per modificare un'area del modulo importata, non esiste alcun modo per cambiare il modificatore di un controllo nella finestra **Proprietà** .  
  
 Per consentire l'accesso a un controllo dall'esterno del file di codice dell'area del modulo, creare una proprietà in tale file di codice per la restituzione del controllo.  
  
 Per ulteriori informazioni su come creare proprietà in c#, vedere [procedura: dichiarare e utilizzare lettura scrivere proprietà &#40; C &#35; Guida per programmatori &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  
  
 Per ulteriori informazioni su come creare proprietà in Visual Basic, vedere [procedura: creare una proprietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Procedura: impedire la visualizzazione di un'area del modulo](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  