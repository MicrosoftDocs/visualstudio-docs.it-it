---
title: Personalizzazione di una barra multifunzione per InfoPath | Documenti Microsoft
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
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 40cf51fce578540a5ea27a96e3482e5d7f906754
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="customizing-a-ribbon-for-infopath"></a>Personalizzazione di una barra multifunzione per InfoPath
  Quando si personalizza la barra multifunzione in Microsoft Office InfoPath, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione. In[!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] è possibile visualizzare la barra multifunzione nei tre tipi seguenti di finestre dell'applicazione InfoPath:  
  
-   Finestre in cui viene visualizzato un modello di form aperto in modalità di progettazione.  
  
-   Finestre in cui è visualizzato un form basato su un modello di form.  
  
-   Finestra Anteprima di stampa.  
  
 **Si applica a:** le informazioni in questo argomento si applicano a progetti di componente aggiuntivo VSTO per InfoPath 2010. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Utenti e progettisti aprono un modello di form in modalità di progettazione per modificarne l'aspetto e il layout. Gli utenti aprono i form basati su un modello di form per aggiungere contenuto.  
  
 La finestra Anteprima di stampa consente ai progettisti e agli utenti di visualizzare in anteprima le pagine di un form o di un modello di form prima della stampa.  
  
> [!NOTE]  
>  La scheda **AddIns** non è presente nella finestra Anteprima di stampa. Se si vuole visualizzare una scheda personalizzata nella finestra Anteprima di stampa, verificare che la proprietà **OfficeId** della scheda non sia impostata su **TabAddIns**.  
  
 È necessario specificare il tipo di barra multifunzione di ogni finestra in cui si vuole visualizzare la barra multifunzione.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Specifica del tipo di barra multifunzione nella finestra di progettazione della barra multifunzione  
 Se si usa l'elemento **Barra multifunzione (finestra di progettazione visiva)** , fare clic sulla proprietà **RibbonType** della barra multifunzione nella finestra **Proprietà** , quindi selezionare uno degli ID indicati nella tabella seguente.  
  
|ID della barra multifunzione|Finestra in cui verrà visualizzata la barra multifunzione all'esecuzione del progetto|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Finestre in cui viene visualizzato un modello di form aperto in modalità di progettazione.|  
|**Microsoft.InfoPath.Editor**|Finestre in cui è visualizzato un form basato su un modello di form.|  
|**Microsoft.InfoPath.PrintPreview**|Finestra Anteprima di stampa.|  
  
 È possibile aggiungere più barre multifunzione a un progetto. Se più barre multifunzione condivide uno stesso ID, eseguire l'override del metodo CreateRibbonExtensibilityObject nella `ThisAddin` classe del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione. Per ulteriori informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Specifica del tipo di barra multifunzione con l'elemento XML della barra multifunzione  
 Se si usa l'elemento **Barra multifunzione (XML)** , controllare il valore del parametro *ribbonID* nel metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> e restituire la barra multifunzione appropriata.  
  
 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione. Il parametro *ribbonID* è una stringa che identifica il tipo di finestra di InfoPath che viene aperto.  
  
 Nell'esempio di codice seguente viene illustrato come visualizzare una barra multifunzione personalizzata solo in una finestra che visualizza un modello di form in modalità di progettazione. La barra multifunzione da visualizzare viene specificata nel metodo `GetResourceText()` , generato nella classe Ribbon. Per altre informazioni sulla classe Ribbon, vedere [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [XML della barra multifunzione](../vsto/ribbon-xml.md)  
  
  