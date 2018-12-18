---
title: 'Procedura: aprire il file di testo come cartelle di lavoro | Documenti Microsoft'
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
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 45d2b85ea8c005d56ddc076d0b758a0c9e4a2d67
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Procedura: aprire file di testo come cartelle di lavoro a livello di codice
  È possibile aprire un file di testo come una cartella di lavoro. È necessario passare il nome del file di testo che si desidera aprire. È possibile specificare diversi parametri facoltativi, ad esempio il numero di riga per iniziare l'analisi e il formato della colonna di dati nel file.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 In questo esempio richiede i seguenti componenti:  
  
-   Un file di testo delimitato da virgole denominato `Test.txt` che contiene almeno tre righe di testo.  
  
-   Il file di testo `Test.txt` siano archiviati nell'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: salvare a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: chiudere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  