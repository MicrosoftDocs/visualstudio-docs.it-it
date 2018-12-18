---
title: Le gerarchie in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d1f018b9cc48d059761a26721c808024f60bb3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) consente di visualizzare un progetto come un *gerarchia*. Nell'IDE, in una gerarchia è una struttura ad albero di nodi, in cui ogni nodo dispone di un set di proprietà associate. Oggetto *gerarchia del progetto* è un contenitore che contiene gli elementi del progetto, le relazioni, degli elementi e delle proprietà dell'elemento associato e comandi.  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gestire le gerarchie di progetto tramite l'interfaccia di gerarchia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia reindirizza i comandi si richiama da elementi di progetto nella finestra gerarchia appropriata anziché il gestore del comando standard.  
  
## <a name="project-hierarchies"></a>Gerarchie di progetto  
 Ogni gerarchia del progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi dipendono dal tipo di progetto. Ad esempio, un progetto di database potrà contenere stored procedure, viste di database e tabelle di database. Un progetto di linguaggio di programmazione, d'altra parte, probabilmente includerà i file di origine e file di risorse per finestre di dialogo e bitmap. Le gerarchie possono essere annidate, che consente una flessibilità aggiunta quando si crea una gerarchia del progetto.  
  
 Quando si crea un nuovo tipo di progetto, il tipo di progetto determina il set completo di elementi che può essere modificato in essa contenuti. Tuttavia, i progetti possono contenere elementi per cui non dispongono supporto per la modifica. Ad esempio, i progetti di Visual C++ possono contenere file HTML, anche se Visual C++ non fornisce un editor personalizzato per il tipo di file HTML.  
  
 Gerarchie di gestiscono la persistenza di elementi in che essi contenuti. L'implementazione della gerarchia deve controllare qualsiasi proprietà speciali che interessano la persistenza degli elementi all'interno della gerarchia. Ad esempio, se gli elementi rappresentano gli oggetti in un repository anziché file, l'implementazione della gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indirizza la gerarchia per salvare gli elementi in conformità con l'input dell'utente, ma non controlla le eventuali azioni necessarie per salvare gli elementi dell'IDE. Al contrario, il progetto è nel controllo.  
  
 Quando un utente apre un elemento in un editor, la gerarchia che controlla tale elemento è selezionata e diventa la gerarchia active. La gerarchia selezionata determina il set di comandi disponibili per intervenire sull'elemento. Rilevamento stato attivo in questo modo consente la gerarchia in modo da riflettere il contesto dell'utente corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di progetto](../../extensibility/internals/project-types.md)   
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Esempi di VSSDK](http://aka.ms/vs2015sdksamples)