---
title: 'Procedura: creazione di nuovi documenti di Visio a livello di codice | Documenti Microsoft'
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 072a279bd342f60f8ebfb307a880c39bdc8b2d51
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Procedura: Creare nuovi documenti di Visio a livello di codice
  Quando si crea un nuovo disegno di Microsoft Office Visio, aggiungerlo alla raccolta Documents dei documenti di Visio aperti. Di conseguenza, il metodo Interop crea un nuovo documento di disegno di Visio. Per altre informazioni, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="creating-new-blank-documents"></a>Creazione di nuovi documenti vuoti  
  
#### <a name="to-create-a-new-document"></a>Per creare un nuovo documento  
  
-   Utilizzare il metodo Interop per creare un nuovo documento vuoto che non si basa su un modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Creazione di documenti copiati da documenti esistenti  
 Il metodo Interop è possibile creare un nuovo documento che è una copia di un documento di Visio esistente. È necessario specificare il nome file e il percorso completo del diagramma.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Per creare un nuovo documento copiato da un documento esistente  
  
-   Chiamare il metodo Interop e specificare il percorso del diagramma di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Creazione di stencil copiati da stencil esistenti  
 Il metodo [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) può creare un nuovo stencil che è una copia di uno stencil di Visio esistente. È necessario specificare il nome file e il percorso completo dello stencil.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Per creare un nuovo stencil copiato da uno stencil esistente  
  
-   Chiamare il metodo Interop e specificare il percorso dello stencil.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Creazione di documenti basati su modelli esistenti  
 Il metodo Interop è possibile creare un nuovo documento (un file con estensione vsd) basato su un modello di Visio esistente (un file con estensione vst). Questo metodo copia gli stencil, gli stili e le impostazioni che fanno parte dell'area di lavoro modello. È necessario specificare il nome file e il percorso completo del modello.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Per creare un nuovo documento basato su un modello esistente  
  
-   Chiamare il metodo Interop e specificare il percorso del modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Deve essere presente un documento di Visio denominato `myDrawing.vsd` in una directory denominata `Test` nella cartella Documenti.  
  
-   Deve essere presente un documento di Visio denominato `myStencil.vss` in una directory denominata `Test` nella cartella Documenti.  
  
-   Deve essere presente un documento di Visio denominato `myTemplate.vst` in una directory denominata `Test` nella cartella Documenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: salvare a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  