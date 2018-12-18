---
title: Estendere il modello a oggetti del progetto di Base | Documenti Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9cffbecf585f6f8be4174531a91e466f65ab9a72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di Base

Un sottotipo di progetto può estendere il modello oggetto di automazione del progetto di base nelle seguenti posizioni:

-   Project.Extender ("\<ProjectSubtypeName >"), in questo modo un sottotipo di progetto offrire un oggetto con metodi personalizzati dal <xref:EnvDTE.Project>. Un sottotipo di progetto è possibile utilizzare le estensioni di automazione per esporre il `Project` oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >"), in questo modo un sottotipo di progetto di offrire un oggetto con metodi personalizzati da un particolare <xref:EnvDTE.ProjectItem> oggetto all'interno del progetto. Un sottotipo di progetto è possibile utilizzare Extender di automazione per esporre questo oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata in Sil aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un desiderato <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Questa raccolta di Project. Properties - espone le proprietà di indipendenti dalla configurazione del `Project` oggetto. Per ulteriori informazioni sulle proprietà di progetto, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto è possibile utilizzare le estensioni di automazione per aggiungere le proprietà per questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_BrowseObjectCATID` da VSHPROPID2 (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration. Properties - questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una particolare configurazione (ad esempio, Debug). Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto è possibile utilizzare le estensioni di automazione per aggiungere le proprietà per questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale offre il relativo oggetto per il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaccia viene utilizzata per distinguere un oggetto di esplorazione di configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>