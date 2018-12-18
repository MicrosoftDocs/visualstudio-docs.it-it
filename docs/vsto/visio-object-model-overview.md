---
title: Panoramica del modello a oggetti di Visio | Documenti Microsoft
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
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e829842f4e530b014a19f69c567a91dc49bd78e6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="visio-object-model-overview"></a>Panoramica del modello a oggetti di Visio
  Per sviluppare soluzioni Office per Microsoft Office Visio è possibile interagire con il modello a oggetti di Visio. Questo modello a oggetti è costituito da classi e interfacce che sono definite nello spazio dei nomi Interop e vengono fornite nell'assembly di interoperabilità primario per Visio.  
  
 Questo argomento contiene una breve panoramica del modello a oggetti di Visio. Per informazioni sull'uso del modello a oggetti di Visio per eseguire attività nei progetti di Office, vedere gli argomenti seguenti:  
  
-   [Uso di documenti di Visio](../vsto/working-with-visio-documents.md)  
  
-   [Uso di forme di Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understanding-the-visio-object-model"></a>Informazioni sul modello a oggetti di Visio  
 In Visio sono disponibili numerosi oggetti con cui è possibile interagire. Questi oggetti sono organizzati in una gerarchia che corrisponde strettamente all'interfaccia utente. Il vertice della gerarchia è occupato dall'oggetto [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx) . Questo oggetto rappresenta l'istanza corrente di Visio. L'oggetto Interop contiene gli oggetti di Microsoft e Microsoft.Office.Interop.Visio.Page, nonché il Documents e Raccolte di Pages. È possibile modificare e usare ogni oggetto e raccolta con i numerosi metodi e le varie proprietà di cui dispone.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA sugli oggetti [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx), [Microsoft.Office.Interop.Visio.Document](https://msdn.microsoft.com/library/office/ff765575.aspx)e [Microsoft.Office.Interop.Visio.Page](https://msdn.microsoft.com/library/office/ff767035.aspx) nonché sulle raccolte [Microsoft.Office.Interop.Visio.Documents](https://msdn.microsoft.com/library/office/ff768812.aspx) e [Microsoft.Office.Interop.Visio.Pages](https://msdn.microsoft.com/library/office/ff766165.aspx) .  
  
 Le sezioni riportate di seguito forniscono una breve descrizione degli oggetti di livello superiore e della loro reciproca interazione. Tali oggetti comprendono quelli elencati di seguito:  
  
-   Oggetto Application  
  
-   Oggetto Document  
  
-   Oggetto Page  
  
### <a name="application-object"></a>Oggetto Application  
 L'oggetto Interop rappresenta l'applicazione Visio ed è l'elemento padre di tutti gli altri oggetti. I membri di tale oggetto in genere vengono applicati a Visio nel suo complesso. È possibile utilizzare le proprietà e metodi degli oggetti Microsoft.Office.Interop.Visio.ApplicationSettings e di Interop per controllare l'ambiente di Visio.  
  
 Nei progetti di componente aggiuntivo VSTO, è possibile accedere all'oggetto Interop utilizzando il `Application` campo la `ThisAddIn` classe. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Oggetto Document  
 L'oggetto di Microsoft è centrale della programmazione di Visio. Rappresenta un disegno, uno stencil o un file modello. Quando si apre un documento di Visio o creare un nuovo documento, si crea un nuovo oggetto di Microsoft, che viene aggiunto alla raccolta Documents dell'oggetto Interop .  
  
 Il documento con lo stato attivo è definito documento attivo. È rappresentato dalla proprietà dell'oggetto Interop Microsoft.Office.Interop.Visio.Application.ActiveDocument.  
  
### <a name="page-object"></a>Oggetto Page  
 L'oggetto Microsoft.Office.Interop.Visio.Page rappresenta l'area di disegno di una pagina di primo piano o di una pagina di sfondo. È possibile utilizzare la proprietà di Interop per determinare se una pagina è una pagina di primo piano o in background.  
  
 Per creare forme, è possibile utilizzare i metodi che includono i metodi Microsoft.Office.Interop.Visio.Page.DrawSpline e Microsoft.Office.Interop.Visio.Page.DrawOval. Inoltre, è possibile recuperare master dagli stencil e posizionare le forme in una pagina utilizzando i metodi DROP o DropMany.  
  
## <a name="using-the-visio-object-model-documentation"></a>Uso della documentazione del modello a oggetti di Visio  
 Per informazioni complete sul modello a oggetti di Visio, vedere la documentazione di riferimento del modello a oggetti di VBA. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Visio esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [Riferimento del modello a oggetti di Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti di VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Visio. Ad esempio, l'oggetto documento nel riferimento del modello a oggetti VBA corrisponde al tipo di Microsoft nell'assembly di interoperabilità primario di Visio. Nonostante il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# per usarli in un progetto di componente aggiuntivo VSTO di Visio creato con Visual Studio.  
  
> [!NOTE]  
>  Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Visio.  
  
 Per esempi di codice correlati e strumenti aggiuntivi per creare soluzioni di Visio, vedere [Visio 2010 Software Development Kit](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Tipi aggiuntivi negli assembly di interoperabilità primari  
 È possibile cercare negli assembly di interoperabilità primari tipi che non sono visibili a VBA a causa delle differenze di implementazione. VBA offre una visualizzazione del modello a oggetti di Visio che include solo gli oggetti e i membri che è possibile usare direttamente. Gli assembly di interoperabilità primari espongono lo stesso modello a oggetti, ma includono anche le altre interfacce, classi e membri che traducono gli oggetti del modello a oggetti COM nel codice gestito. Questi elementi aggiuntivi non devono essere usati direttamente nel codice.  
  
 Per altre informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592) e [Office Primary Interop Assemblies](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Utilizzo di documenti di Visio](../vsto/working-with-visio-documents.md)   
 [Uso di forme di Visio](../vsto/working-with-visio-shapes.md)  
  
  