---
title: Automazione per la configurazione e oggetti SelectedItem | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a9446a5c63df7f20d6e4dbdc3cb60bf20183bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per la configurazione e oggetti SelectedItem
È possibile automatizzare la compilazione e l'elemento selezionato di processi in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automazione per le compilazioni  
 Compilazione o la configurazione è disponibile un modello di automazione che viene fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).  
  
 Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario utilizzare il modello di automazione.  
  
## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem  
 Non è necessario fornire un'implementazione per il `SelectedItem` perché Visual Studio contiene un'implementazione standard dell'oggetto. Tuttavia, è possibile implementare il `SelectedItem` dell'oggetto se si preferisce. È necessario implementare un oggetto che contiene il `SelectedItem` interfaccia e restituire una risposta a una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> con VSITEMID impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Che contribuiscono al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)