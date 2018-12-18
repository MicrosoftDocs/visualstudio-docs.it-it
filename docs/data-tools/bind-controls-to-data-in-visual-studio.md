---
title: Associare i controlli ai dati in Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: d6a1ab26dc402d039a5e858896ec25668be8df9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Associare i controlli ai dati in Visual Studio
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli. È possibile creare questi controlli con associazione a dati trascinando elementi dal **origini dati** finestra in un'area di progettazione o controlli su una superficie in Visual Studio.  
  
 In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati. Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati. Per informazioni più dettagliate su come creare controlli associati a dati, vedere [controlli binding di Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
## <a name="data-sources"></a>Origini dati  
 Nel contesto di associazione dati, un'origine dati rappresenta i dati in memoria che può essere associato a un'interfaccia utente. In pratica, un'origine dati può essere una classe di Entity Framework, un set di dati, un endpoint del servizio che viene incapsulato in un oggetto proxy .NET, una classe LINQ to SQL, o qualsiasi oggetto .NET o raccolta. Alcune origini dati consentono di creare controlli associati a dati trascinando elementi dal **origini dati** finestra, mentre altre origini dati non. Nella tabella seguente vengono indicate le origini dati supportate.  
  
|Origine dati|Supporto di trascinamento e rilascio in **Progettazione Windows Form**|Supporto di trascinamento e rilascio in **WPF Designer**|Supporto di trascinamento e rilascio in **Silverlight Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Set di dati|Yes|Sì|No|  
|Entity Data Model|Sì<sup>1</sup>|Yes|Yes|  
|Classi LINQ to SQL|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|Servizi (inclusi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF services e i servizi web)|Yes|Sì|Yes|  
|Object|Yes|Sì|Yes|  
|SharePoint|Yes|Sì|Yes|  
  
 1. Generare il modello utilizzando il **Entity Data Model** procedura guidata, quindi trascinare tali oggetti nella finestra di progettazione.  
  
 2. Classi LINQ to SQL non vengono visualizzati il **origini dati** finestra. È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="data-sources-window"></a>Finestra Origini dati  
 Origini dati sono disponibili per il progetto come elementi di **origini dati** finestra. Questa finestra è visibile o accessibile dal **vista** menu, quando un'area di progettazione del form è la finestra attiva nel progetto. È possibile trascinare elementi da questa finestra per creare controlli associati ai dati sottostanti e facendovi clic sopra, è inoltre possibile configurare le origini dati.  
  
 ![Finestra Origini dati](../data-tools/media/raddata-data-sources-window.png "finestra Origini dati raddata")  
  
 Per ogni tipo di dati che viene visualizzato nel **origini dati** finestra, viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione. Prima di trascinare un elemento di **origini dati** finestra, è possibile modificare il controllo che verrà creato. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Attività coinvolte nell'associazione di controlli ai dati  
 Nella tabella seguente sono elencate alcune delle attività più comuni eseguite per associare i controlli ai dati.  
  
|Attività|Altre informazioni|  
|----------|----------------------|  
|Aprire il **origini dati** finestra.|Aprire un'area di progettazione nell'editor e scegliere **vista** > **origini dati**.|  
|Aggiungere un'origine dati al progetto.|[Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)|  
|Impostare il controllo che viene creato quando si trascina un elemento di **origini dati** finestra alla finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modificare l'elenco dei controlli associati a elementi di **origini dati** finestra.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Creare controlli associati a dati.|[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|  
|Associare a un oggetto o una raccolta.|[Associare oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtrare i dati che viene visualizzato nell'interfaccia utente.|[Filtrare e ordinare i dati in un'applicazione Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Personalizzare le didascalie per i controlli.|[Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio data tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  (Strumenti dati di Visual Studio per .NET)  
 [Data binding in Windows Form](/dotnet/framework/winforms/windows-forms-data-binding)