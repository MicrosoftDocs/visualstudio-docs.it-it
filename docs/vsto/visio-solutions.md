---
title: Soluzioni Visio | Documenti Microsoft
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
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 558ddc7a9c0fee5305052143edaca2b88b097723
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="visio-solutions"></a>Soluzioni Visio
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Visio. È possibile usare i componenti aggiuntivi VSTO per automatizzare Visio, estenderne le funzionalità o personalizzarne l'interfaccia utente Visio.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Se ha esperienza di programmazione con Microsoft Office, vedere [introduzione &#40; sviluppo per Office in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Si applica a:** le informazioni in questo argomento si applicano a progetti di componente aggiuntivo VSTO per Visio 2010. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>Automazione di Visio usando il modello a oggetti di Visio  
 Il modello a oggetti di Visio espone molte classi utilizzabili per automatizzare Visio affinché crei diagrammi per risorse di vario tipo, fra cui organigrammi, diagrammi di flusso, pianificazioni di progetto, diagrammi di rete e spazi di ufficio. L'API consente di scrivere codice per eseguire attività comuni:  
  
-   Creare e posizionare forme e testo nei diagrammi.  
  
-   Gestire il comportamento delle forme in base alla logica di business e all'input dell'utente.  
  
-   Controllare la visualizzazione dei diagrammi, ad esempio mediante panoramica e zoom.  
  
-   Personalizzare l'interfaccia utente dell'applicazione.  
  
-   Importare dati esterni in Visio, connetterli a forme e visualizzarli graficamente in una pagina.  
  
 È possibile visualizzare procedure dettagliate ed esempi di codice per usare il modello a oggetti di Visio per usare documenti e forme in [Working with Visio Documents](../vsto/working-with-visio-documents.md) e [Working with Visio Shapes](../vsto/working-with-visio-shapes.md).  
  
 Per accedere al modello a oggetti di Visio da un componente aggiuntivo VSTO, usare nel progetto il campo `Application` della classe `ThisAddIn` . Il `Application` campo restituisce un oggetto Interop che rappresenta l'istanza corrente di Visio. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di Visio, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario (PIA) per Visio. L'assembly di interoperabilità primario funge da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Visio. Tutti i tipi nell'assembly di interoperabilità primario di Visio sono definiti nello spazio dei nomi Interop. Per ulteriori informazioni sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Panoramica del modello a oggetti di Visio  
 È possibile trovare una panoramica del modello a oggetti Visio in [Visio Object Model Overview](../vsto/visio-object-model-overview.md), che include i collegamenti al riferimento del modello a oggetti Visio e agli SDK.  
  
## <a name="customizing-the-user-interface-of-visio"></a>Personalizzazione dell'interfaccia utente di Visio  
 L'interfaccia utente di Visio offre le opzioni di personalizzazione seguenti.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
  
 Per informazioni sulla personalizzazione dell'interfaccia utente di Visio, vedere la documentazione di riferimento di VBA relativa alla classe [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) .  
  
## <a name="see-also"></a>Vedere anche  
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Cenni preliminari sullo sviluppo di soluzioni Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  