---
title: 'Procedura: scorrere i record del Database in un foglio di lavoro | Documenti Microsoft'
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Procedura: scorrere i record di un database in un foglio di lavoro
  La procedura seguente viene illustrato come utilizzare la finestra di progettazione per visualizzare un singolo campo di una tabella di database in un foglio di lavoro di Microsoft Office Excel, con i controlli che consentono all'utente di scorrere tutti i record.  
  
 È possibile utilizzare la finestra di progettazione solo nei progetti a livello di documento. Tuttavia, è possibile aggiungere controlli e associarli ai dati a livello di codice in fase di esecuzione. Per ulteriori informazioni, vedere [procedura dettagliata: Data Binding semplice in VSTO aggiuntivo progetto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Per scorrere i record del database in un foglio di lavoro  
  
1.  Aprire un progetto di applicazione di Excel in Visual Studio.  
  
2.  Aprire il **origini dati** finestra e creare un'origine dati dal database. Per ulteriori informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).  
  
3.  Espandere la tabella che contiene i dati che si desidera visualizzare e selezionare la colonna specifica.  
  
4.  Aprire l'elenco di controlli e scegliere **NamedRange**.  
  
5.  Trascinare il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella in cui si desidera visualizzare i dati.  
  
6.  Dal **Windows Form** scheda della finestra di **della casella degli strumenti**, aggiungere un <xref:System.Windows.Forms.BindingNavigator> al foglio di lavoro e impostare i controlli che si desidera utilizzare. Per ulteriori informazioni, vedere [Cenni preliminari sul controllo BindingNavigator &#40; Windows Form &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  