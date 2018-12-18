---
title: Fornisce un contesto del servizio di linguaggio tramite l'API Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3556fcce3d14d5069854c64d81cb780123a979d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fornisce un contesto del servizio di linguaggio tramite l'API Legacy
Sono disponibili due opzioni per un servizio di linguaggio fornire contesto utente utilizzando il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale: fornire un contesto di indicatore di testo, o fornire un contesto utente tutti. In seguito vengono descritte le differenze tra ogni.  
  
 Per ulteriori informazioni sulla fornitura di contesto a un servizio di linguaggio che è connesso a un editor personalizzato, vedere [procedura: fornire contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fornire un contesto di indicatore di testo nell'editor  
 Per fornire il contesto per gli errori del compilatore indicati dai marcatori di testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core editor, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia. In questo scenario, il servizio di linguaggio fornisce il contesto solo quando il cursore si trova in un indicatore di testo. In questo modo l'editor fornire la parola chiave in corrispondenza del cursore ai **Guida dinamica** finestra senza attributi.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fornire tutto il contesto utente nell'editor  
 Se si sta creando un servizio di linguaggio e si utilizza il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core editor, è possibile implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia per fornire il contesto per il servizio di linguaggio.  
  
 Per l'implementazione di `IVsLanguageContextProvider`, dell'editor, responsabile per l'aggiornamento dei contesti collegato un elenco di contesti (raccolta). Quando il **Guida dinamica** finestra chiamate di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaccia su questo contenitore di contesto nel tempo di inattività, contesti esegue una query dell'editor per un aggiornamento. L'editor notifica quindi il servizio di linguaggio che deve aggiornare l'editor e passa un puntatore a contesti. Questa operazione viene eseguita chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metodo dall'editor per il servizio di linguaggio. Utilizzo del puntatore per contesti, il servizio di linguaggio può ora aggiungere e rimuovere gli attributi e le parole chiave. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Esistono due diversi modi per implementare `IVsLanguageContextProvider`:  
  
-   Fornire una parola chiave per i contesti  
  
     Quando l'editor viene chiamato per aggiornare l'elenco di contesti, passare gli attributi e le parole chiave appropriate e quindi restituire `S_OK`. Questo valore restituito indica l'editor per mantenere il contesto della parola chiave e l'attributo invece di fornire la parola chiave in corrispondenza del cursore di contesti.  
  
-   Ottenere la parola chiave dalla parola chiave in corrispondenza del cursore  
  
     Quando l'editor viene chiamato per aggiornare l'elenco di contesti, passare gli attributi appropriati e quindi restituire `E_FAIL`. Questo valore restituito indica l'editor per mantenere gli attributi in contesti, ma aggiornare contesti con la parola chiave in corrispondenza del cursore.  
  
 Il diagramma seguente illustra come contesto viene fornito per un servizio di linguaggio che implementa `IVsLanguageContextProvider`.  
  
 ![Immagine di LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contesto per un servizio di linguaggio  
  
 Come è possibile visualizzare nel diagramma, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di testo di base ha un elenco di contesti collegato. Questo elenco di contesti punta a tre contenitori separati sottocontesto: servizio di linguaggio, l'editor predefinito e indicatore di testo. I contenitori language service e il testo marcatore sottocontesto contengono gli attributi e le parole chiave per il servizio di linguaggio se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaccia viene implementata e marcatori di testo se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaccia è implementata. Se non si implementa una di queste interfacce, l'editor fornisce contesto per la parola chiave in corrispondenza del cursore nel contenitore sottocontesto editor predefinito.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Linee guida di contesto per gli editor e finestre di progettazione  
 Editor e finestre di progettazione deve fornire una parola chiave generale per l'editor o finestra di progettazione. Questa operazione viene eseguita in modo che un argomento generico, ma appropriato, verrà visualizzato per l'editor o finestra di progettazione quando l'utente preme F1. Un editor deve, oltre a ciò, la parola chiave corrente in corrispondenza del cursore o forniscano un termine chiave in base alla selezione corrente. Questa operazione viene eseguita per garantire che un argomento della Guida per il testo o un elemento dell'interfaccia utente a cui punta oppure selezionata viene visualizzata quando l'utente preme F1. Una finestra di progettazione fornisce contesto per un elemento selezionato in una finestra di progettazione, ad esempio un pulsante in un form. Gli editor e finestre di progettazione deve connettersi anche a un servizio di linguaggio come descritto [Legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).