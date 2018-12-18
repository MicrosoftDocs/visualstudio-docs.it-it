---
title: Soluzioni PowerPoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3808ecf78e8a7e110561c558a6278ee4873843c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="powerpoint-solutions"></a>Soluzioni PowerPoint
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Se si ha familiarità con la programmazione con Microsoft Office, vedere [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [come ricerca per categorie: crea un componente aggiuntivo per Microsoft PowerPoint?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automating-powerpoint-by-using-the-powerpoint-object-model"></a>Automazione di PowerPoint usando il modello a oggetti di PowerPoint  
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:  
  
-   Creare e formattare presentazioni a livello di codice.  
  
-   Aggiungere o rimuovere diapositive dalle presentazioni.  
  
-   Aggiungere o modificare forme su una diapositiva.  
  
 Per accedere al modello a oggetti di PowerPoint da un componente aggiuntivo VSTO, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Application> che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi dell'assembly di interoperabilità primario di PowerPoint sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.PowerPoint> . Per ulteriori informazioni sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Uso della documentazione del modello a oggetti di PowerPoint  
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario (PIA) di PowerPoint e il riferimento del modello a oggetti VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Riferimento dell'assembly di interoperabilità primario  
 Nella documentazione di riferimento dell'assembly di interoperabilità primario (PIA) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile al seguente percorso: [Riferimento dell'assembly di interoperabilità primario di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Per altre informazioni sulla progettazione dell'assembly di interoperabilità primario (PIA) di PowerPoint, ad esempio sulle differenze tra classi e interfacce nell'assembly di interoperabilità primario (PIA) e sulla modalità di implementazione degli eventi nell'assembly di interoperabilità primario (PIA), vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [Riferimento del modello a oggetti di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di PowerPoint. Ad esempio, l'oggetto di presentazione nel riferimento del modello a oggetti VBA corrisponde al <xref:Microsoft.Office.Interop.PowerPoint.Presentation> tipo nell'assembly di interoperabilità primario di PowerPoint. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.  
  
## <a name="customizing-the-user-interface-of-powerpoint"></a>Personalizzazione dell'interfaccia utente di PowerPoint  
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Aggiungere schede personalizzate alla barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: Personalizzare una scheda predefinita](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione del primo VSTO aggiuntivo per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Cenni preliminari sullo sviluppo di soluzioni di Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  