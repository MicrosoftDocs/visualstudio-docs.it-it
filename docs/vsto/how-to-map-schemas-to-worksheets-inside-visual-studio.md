---
title: "Procedura: mappare schemi a fogli di lavoro all'interno di Visual Studio | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2d0caadfc08d7fa1d2ea29d04e84a5d954a42fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procedura: mappare schemi a fogli di lavoro in Visual Studio
  È possibile eseguire il mapping uno schema XML a un foglio di lavoro mentre il foglio di lavoro è aperta in Visual Studio. Utilizzare gli stessi strumenti di Microsoft Office Excel utilizzata per la cartella di lavoro è aperto all'esterno di Visual Studio. Se si esegue il mapping dello schema al foglio di lavoro prima o dopo aver creato la soluzione di Excel, il progetto di Office crea gli stessi oggetti.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  È possibile utilizzare schemi XML multipart nelle soluzioni Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Eseguire il mapping di uno schema XML a un foglio di lavoro di Excel in Visual Studio  
  
1.  Aprire il progetto di modello o cartella di lavoro di Excel in Visual Studio.  
  
2.  Fare clic su per spostare lo stato attivo alla finestra di progettazione del foglio di lavoro.  
  
3.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Nel **XML** gruppo, fare clic su **origine**.  
  
     Il **origine XML** verrà visualizzata la finestra.  
  
5.  Nel **origine XML** finestra, fare clic su **mapping XML**.  
  
     Il **mapping XML** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **mapping XML** la finestra di dialogo, fare clic su **Aggiungi**.  
  
7.  Individuare il file di schema, selezionarlo e quindi fare clic su **aprire**.  
  
8.  Fare clic su **OK**.  
  
     Lo schema è rappresentato nel **origine XML** finestra. Nel progetto di un oggetto tipizzato <xref:System.Data.DataSet> viene generato in base allo schema e un <xref:System.Windows.Forms.BindingSource> viene creato.  
  
9. Trascinare gli elementi dal **origine XML** finestra a posizioni nel foglio di lavoro in cui si desidera creare i corrispondenti controlli.  
  
     Se si trascina un elemento dello schema non ripetuto, il progetto di Office genera un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo che viene associato automaticamente il <xref:System.Windows.Forms.BindingSource>.  
  
     Se si trascina un elemento ripetuto dello schema, il progetto di Office genera un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo che non viene associato automaticamente a un'origine dati. Per ulteriori informazioni, vedere [schemi e dati nelle personalizzazioni a livello di documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  