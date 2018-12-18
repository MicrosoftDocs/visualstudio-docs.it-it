---
title: Estensione del sistema di progetto SharePoint | Documenti Microsoft
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
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e79808ef9d5d4712d67426b202046615c8ab14b2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-project-system"></a>Estensione del sistema di progetto SharePoint
  È possibile creare soluzioni di SharePoint utilizzando un set di modelli di progetto e modelli di elementi in Visual Studio. Questi modelli di soddisfano i requisiti di numerosi scenari di sviluppo, ma è possibile individuare alcuni casi in cui non dispongono della funzionalità desiderata. In questi casi, è possibile estendere il sistema di progetto SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Panoramica del sistema del progetto SharePoint  
 Il sistema di progetto SharePoint si basa sul componente fondamentale di *elementi di progetto SharePoint*. Un elemento di progetto SharePoint rappresenta una singola personalizzazione di SharePoint, ad esempio una definizione di elenco, una Web Part o un tipo di contenuto.  
  
 Un progetto di SharePoint è un progetto di Visual Studio che include uno o più elementi di progetto SharePoint. Progetti di SharePoint contengono anche i componenti aggiuntivi che definiscono la modalità di raggruppamento di elementi di progetto in funzionalità e pacchetti per la distribuzione.  
  
 Per ulteriori informazioni sul contenuto di elementi di progetto SharePoint e i progetti SharePoint, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Come estendere il sistema di progetto SharePoint  
 È possibile estendere il sistema di progetto SharePoint nei modi seguenti:  
  
-   Definire i propri tipi di elemento di progetto SharePoint e associarli a nuovi modelli di elemento o i modelli di progetto in Visual Studio. Ad esempio, è possibile definire un tipo di elemento di progetto SharePoint per la creazione di un'azione personalizzata o un campo. Per ulteriori informazioni, vedere [tipi di elemento di definizione personalizzato SharePoint progetto](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Estendere i tipi di elemento di progetto SharePoint sono già installati in Visual Studio. Ad esempio, è possibile aggiungere una voce di menu di scelta rapida a un elemento di progetto in **Esplora** e personalizzare l'elemento del progetto quando uno sviluppatore sceglie la voce di menu. Per ulteriori informazioni, vedere [estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Estendere i progetti SharePoint. Ad esempio, è possibile aggiungere i gestori eventi per eseguire attività specifiche, quando gli elementi vengono aggiunti o rimossi dai progetti SharePoint. Per ulteriori informazioni, vedere [estendere i progetti SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Estendere il comportamento di creazione di pacchetti e distribuzione di elementi di progetto SharePoint e i progetti SharePoint. Ad esempio, è possibile creare la propria procedura di distribuzione da eseguire quando si distribuisce o si ritira un progetto o per eseguire attività personalizzate aggiuntive quando Visual Studio esegue alcune operazioni di distribuzione. Per ulteriori informazioni, vedere [estensione SharePoint e distribuzione di pacchetti](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Attività di sviluppo comuni  
 Nelle estensioni del sistema del progetto SharePoint, è possibile eseguire le seguenti operazioni:  
  
-   Salvare i dati di stringa personalizzato con elementi di progetto e in diversi tipi di file di progetto. Per ulteriori informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertire un oggetto nel sistema del progetto SharePoint in un oggetto corrispondente nel modello oggetto di automazione di Visual Studio o modello di integrazione, o viceversa. Per ulteriori informazioni, vedere [la conversione tra sistema di tipi di progetto SharePoint e altri tipi di progetto da Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Distribuzione e l'estensione dei pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  