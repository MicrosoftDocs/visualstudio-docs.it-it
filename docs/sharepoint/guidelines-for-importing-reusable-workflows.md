---
title: Linee guida per l'importazione di flussi di lavoro riutilizzabili | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 57ca59e7e31cabde62128d2e56df45c4819cfb65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Linee guida per l'importazione di flussi di lavoro riutilizzabili
  Per importare flussi di lavoro riutilizzabili creati in SharePoint Designer, utilizzare il modello di progetto Importa flusso di lavoro riutilizzabile di SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Questo modello Importa un *dichiarativa* *flusso di lavoro* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-solo) e lo converte in un *code del flusso di lavoro*, che è un flusso di lavoro che può migliorare con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] codice. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Tuttavia, con il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010 è possibile importare solo soluzioni farm. Se si desidera distribuire il flusso di lavoro come soluzione creata mediante sandbox, importarlo con il modello Importa pacchetto di soluzione SharePoint 2010. Tuttavia, in questo caso, non è possibile convertirlo in un flusso di lavoro di codice e quindi non sarà possibile modificarlo.  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>L'importazione di flussi di lavoro riutilizzabili tramite il modello di flusso di lavoro riutilizzabile di importazione  
 Se si importa un flusso di lavoro riutilizzabile tramite il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010, sarà possibile eseguire o modificare la soluzione proprio come con qualsiasi altra soluzione di SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tuttavia potrebbe essere necessario correggere manualmente alcuni elementi.  
  
### <a name="importing-task-forms"></a>Importazione di moduli attività  
 Con il modello di progetto Importa flusso di lavoro riutilizzabile di SharePoint 2010 vengono importati tutti i form di avvio e associazione, ma viene importato un solo form di attività poiché lo schema del flusso di lavoro di codice consente la presenza di un solo form di questo tipo. Qualsiasi form di attività aggiuntive dalla soluzione del flusso di lavoro originale vengono inseriti il **altri file importati** cartella **Esplora**.  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importazione di flussi di lavoro riutilizzabili tramite il modello Importa pacchetto di soluzione SharePoint 2010  
 Se si importa un flusso di lavoro riutilizzabile tramite il modello Importa pacchetto di soluzione SharePoint 2010, è necessario considerare i problemi riportati di seguito.  
  
-   Dopo aver importato il flusso di lavoro, è possibile distribuire immediatamente ed eseguirlo in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premendo il tasto F5. Tuttavia, se si modifica qualsiasi elemento nel flusso di lavoro nella soluzione importata, potrebbe essere necessario correggere manualmente gli elementi del progetto prima di poter distribuire ed eseguire il flusso di lavoro.  
  
-   Il flusso di lavoro è dichiarativo, codice non è possibile aggiungere ad esso. Per convertire il flusso di lavoro in un flusso di lavoro di codice, è necessario importarlo in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando il modello Importa flusso di riutilizzabile SharePoint 2010.  
  
-   Mentre è possibile modificare il file (con estensione xoml) di progettazione del flusso di lavoro nella visualizzazione progettazione, è consigliabile modificarlo in visualizzazione origine, in quanto la finestra di progettazione del flusso di lavoro visualizza falsi errori.  
  
-   Il debug del flusso di lavoro non funziona per il contenuto dichiarativo. Impostare punti di interruzione [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] non vengono raggiunti.  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>Importazione di soluzioni flusso di lavoro riutilizzabile globalmente  
 Non è possibile importare flussi di lavoro riutilizzabili globalmente tramite il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010. Per importare un flusso di lavoro riutilizzabile globalmente, è necessario convertirlo in un flusso di lavoro riutilizzabile non globalmente o utilizzare il modello Importa pacchetto di soluzione SharePoint 2010.  
  
 Per convertire il flusso di lavoro, creare una copia del flusso di lavoro riutilizzabile globalmente in SharePoint Designer (aprendo il menu di scelta rapida per il flusso di lavoro e quindi scegliendo **Salva come copia**). Successivamente, importare il nuovo flusso di lavoro riutilizzabile con il modello Importa flusso di lavoro riutilizzabile di SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Per importare il flusso di lavoro riutilizzabile globalmente senza modificarlo, utilizzare il modello Importa pacchetto di soluzione SharePoint 2010. Se si utilizza questo metodo, il flusso di lavoro non verrà convertito in un flusso di lavoro di codice e rimarrà un flusso di lavoro dichiarativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  