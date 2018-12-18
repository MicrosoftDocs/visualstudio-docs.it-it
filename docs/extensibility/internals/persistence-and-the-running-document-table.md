---
title: Persistenza e l'esecuzione nel documento tabella | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51f3d2cc41c9adaf97215701ad01da2e59d245a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="persistence-and-the-running-document-table"></a>Persistenza e la tabella Document in esecuzione
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, i progetti sono completamente responsabili della gestione della persistenza di elementi di progetto, che portano a termine utilizzando il servizio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Documenti sono l'unità base di persistenza nell'ambiente di Visual Studio. Progetti di coordinare l'apertura, salvataggio e la ridenominazione di documenti con la tabella documenti in esecuzione (RDT), una risorsa che tiene traccia dello stato di tutti i documenti aperti.  
  
## <a name="managing-persistence"></a>La gestione di persistenza  
 Progetti consentono di controllare il servizio di persistenza dell'ambiente mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaccia. L'ambiente richiede mai direttamente un documento persistente, verrà richiesto il progetto proprietario (o gerarchia) per salvare il documento. Questo rende possibile per il progetto salvare i dati di elemento di progetto in file locali, i file remoti, un database, un repository o altro supporto.  
  
 Ambiente globale viene gestito il RDT. L'ambiente mantiene le voci per tutte le finestre e documenti in RDT, il che rende possibile per poter ricevano notifiche speciali, ad esempio quando la chiusura di una soluzione. Inoltre, il RDT rende possibile per l'ambiente rilevare i nodi corrispondenti nella **Esplora**. Il RDT mantiene un record per ogni oggetto aperto, persistente, inclusi i file di progetto e documenti di elementi di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md)   
 [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)