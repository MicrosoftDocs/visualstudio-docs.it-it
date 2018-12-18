---
title: Soluzioni InfoPath | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9db28542e4141767be55241b98e0a6b762b0e236
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="infopath-solutions"></a>Soluzioni InfoPath
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath non è disponibile in Office 2016.  
  
> [!NOTE]  
>  È comunque possibile creare un componente aggiuntivo VSTO per InfoPath anche se è stato installato Office 2016. È sufficiente installare InfoPath 2013 o Office 2013 side-by-side con Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
 I componenti aggiuntivi VSTO per InfoPath sono simili ai componenti aggiuntivi VSTO per altre applicazioni di Microsoft Office. Questi tipi di soluzioni sono costituiti da un assembly caricato dall'applicazione. Gli utenti finali possono avere accesso alle funzionalità di questo assembly indipendentemente dal modulo o dal modello di modulo aperto. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 non include i progetti del modello di modulo InfoPath forniti nelle versioni precedenti di Visual Studio. Non è nemmeno possibile usare Visual Studio 2015 per aprire o modificare un progetto del modello di modulo InfoPath creato in una versione precedente di Visual Studio. Tuttavia, è possibile aprire e modificare un progetto del modello di modulo InfoPath usando Visual Studio Tools for Applications. Per altre informazioni, vedere [Uso dei progetti VSTO 2008 in InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automating-infopath-by-using-an-add-in"></a>Automazione di InfoPath usando un componente aggiuntivo  
 Per accedere al modello a oggetti InfoPath da un componente aggiuntivo VSTO di Office creato mediante gli strumenti di sviluppo per Office in Visual Studio, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.InfoPath.Application> che rappresenta l'istanza corrente di InfoPath. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti InfoPath da un componente aggiuntivo VSTO, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario per InfoPath. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in InfoPath. Tutti i tipi nell'assembly di interoperabilità primario di InfoPath sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.InfoPath> . Per altre informazioni sull'assembly di interoperabilità primario di InfoPath, vedere [Informazioni sull'assembly di interoperabilità primario di Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Per ulteriori informazioni sugli assembly di interoperabilità primari in generale, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizzazione dell'interfaccia utente di InfoPath usando un componente aggiuntivo  
 Quando si crea un componente aggiuntivo VSTO per InfoPath, sono disponibili varie opzioni di personalizzazione dell'interfaccia utente. Nella tabella riportata di seguito vengono elencate alcune di queste opzioni.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Aggiungere schede personalizzate alla barra multifunzione in InfoPath.|[Personalizzazione di una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di InfoPath e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'assembly di interoperabilità primario di Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Cenni preliminari sullo sviluppo di soluzioni di Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  