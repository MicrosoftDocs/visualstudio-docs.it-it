---
title: Modulo di supporto nei flussi di lavoro | Documenti Microsoft
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
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2544bbe60ea014ee873342f06ce285c809b42eb6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="form-support-in-workflows"></a>Supporto dei form nei flussi di lavoro
  Quattro tipi di moduli possono essere utilizzati in un flusso di lavoro: avvio, l'associazione, attività e modifica. Questi tipi di modulo possono essere basati su un form ASPX o un modulo di InfoPath. Il livello di supporto che [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornisce per un particolare modulo dipende da diversi fattori, che sono descritte nelle tabelle seguenti. Per ulteriori informazioni sui tipi di modulo del flusso di lavoro, vedere [Cenni preliminari sui form del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=185228) nel sito Web MSDN.  
  
## <a name="xml-refactoring"></a>Refactoring di XML  
 Quando si aggiunge un form ASPX associazione o di avvio per un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elemento del progetto flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automaticamente effettua il refactoring del file XML nel file Elements.xml del flusso di lavoro per mantenere l'attributo che fa riferimento al form di associazione o avvio sincronizzato ogni volta che viene aggiornato il percorso di distribuzione o nome di modulo o il modulo è stato eliminato. Tuttavia, quando si usano altri tipi di modulo in un flusso di lavoro, ad esempio un modulo di attività o la modifica, il file Elements.xml non viene effettuato il refactoring.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Supporto dei form nei nuovi flussi di lavoro di Visual Studio  
 La tabella seguente elenca [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il supporto per diversi tipi di form in ASPX o InfoPath nei flussi di lavoro creati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di modulo|Flusso di lavoro creato in Visual Studio con un Form ASPX|Flusso di lavoro creato in Visual Studio tramite un modulo di InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Associazione|-Un form di associazione ASPX può essere aggiunto al flusso di lavoro utilizzando il **Form di associazione del flusso di lavoro** modello di elemento.<br />-Quando il form viene aggiunto, rinominato o eliminato, o il relativo percorso di distribuzione, viene effettuato il refactoring il file Elements.xml del flusso di lavoro.<br />-Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo InfoPath associazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|  
|Avvio|-Un form di avvio ASPX può essere aggiunto al flusso di lavoro utilizzando il **Form di avvio del flusso di lavoro** modello di elemento.<br />-Quando il form viene aggiunto, rinominato o eliminato, o il relativo percorso di distribuzione, viene effettuato il refactoring il file Elements.xml del flusso di lavoro.<br />-Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Non è presente alcun modello di modulo InfoPath associazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|  
|Attività|-Modello di modulo attività nessuna ASPX è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. È necessario creare una pagina dell'applicazione e aggiungere il codice.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.<br />-Per ulteriori informazioni, vedere [moduli delle attività del flusso di lavoro (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Non è presente alcun modello di modulo InfoPath attività in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|  
|Modifica|-Alcun modello di form ASPX modifica non è disponibile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per aggiungere un form di modifica, è necessario creare una pagina dell'applicazione e aggiungere il codice.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring. È necessario modificare manualmente come appropriato.<br />-Per ulteriori informazioni, vedere [form di modifica del flusso di lavoro (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Non è presente alcun modello di modulo InfoPath modifica in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Non è prevista alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e progettazione di InfoPath.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Supporto dei form nei flussi di lavoro riutilizzabile di SharePoint importati  
 La tabella seguente elenca [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il supporto per diversi tipi di form in ASPX o InfoPath in SharePoint flussi di lavoro riutilizzabili che vengono importati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di modulo|Flusso di lavoro riutilizzabile che dispone di un form ASPX importato da SharePoint Designer|Flusso di lavoro riutilizzabile che dispone di un modulo di InfoPath importato da SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Associazione|-Il modulo viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-Quando il form viene rinominato o eliminato, o il relativo percorso di distribuzione, viene effettuato il refactoring il file Elements.xml del flusso di lavoro.|-Il modulo viene importato, ma non viene fatto riferimento nel file Elements. XML del flusso di lavoro.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|  
|Avvio|-Il modulo fa riferimento il flusso di lavoro nel file Elements.xml del flusso di lavoro.<br />-Quando il form viene rinominato o eliminato, o il relativo percorso di distribuzione, viene effettuato il refactoring il file Elements.xml del flusso di lavoro.|-Il modulo viene importato, ma non viene fatto riferimento nel file Elements. XML del flusso di lavoro.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring. **Nota:** regole e le proprietà devono essere aggiunte e modificate per questo scenario.|  
|Attività|-Il modulo viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring.|-Il modulo viene importato, ma non viene fatto riferimento nel file Elements. XML del flusso di lavoro.<br />-Il file Elements.xml del flusso di lavoro non viene eseguito il refactoring. **Nota:** regole e le proprietà devono essere aggiunte e modificate per questo scenario.|  
|Modifica|Non applicabile. Form modifica ASPX non può essere creato in SharePoint Designer.|Non applicabile. Impossibile creare il form di modifica di InfoPath in SharePoint Designer, ad eccezione dell'incorporato SharePoint Server flusso di lavoro che non è incluso nel file con estensione wsp quando viene esportato il flusso di lavoro.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  