---
title: Oggetto VSTextBuffer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 643bd434e058a24cc17936d9ab2f333489b8aa5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vstextbuffer-object"></a>Oggetto VSTextBuffer
L'oggetto TextBuffer rappresenta un flusso di testo Unicode, che in genere è associato un file. Oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere utilizzato all'esterno del contesto dell'editor di componenti di base, come nel caso di una procedura guidata.  
  
 Nella tabella seguente vengono visualizzate le interfacce di `VSTextBuffer`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaccia OLE standard. Utilizzato principalmente per la gestione del buffer di annullamento/ripristino.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaccia OLE standard.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composti (vale a dire, azioni che vengono raggruppate in un'unità singola, annullare o ripristinare).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita la persistenza dei dati del documento gestiti dal buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti clienti.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilizzato per la ricerca di un buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Consente di lettura e scrittura funzionalità usando le coordinate bidimensionali. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Consente di lettura e scrittura funzionalità usando le coordinate unidimensionale. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Accesso veloce, orientato al flusso, sequenziali in testo nel buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome o il moniker, del buffer. È possibile archiviare dati casuali nel buffer con questa interfaccia mediante la creazione di un GUID e l'uso come chiave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta punti di connessione per gli eventi.|  
  
## <a name="remarks"></a>Note  
 Il `VSTextBuffer` è disponibile in genere da un `QueryInterface` chiamare su `IVsTextBuffer`. Per ulteriori informazioni, vedere [Buffer del testo](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)