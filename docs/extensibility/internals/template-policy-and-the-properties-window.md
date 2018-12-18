---
title: Criteri dei modelli e la finestra proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 759864533aa5bd3455a4e01c6642817107abb1a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e la finestra proprietà
Quando un progetto è contenuto all'interno di un progetto di modello enterprise, il progetto di modello enterprise può applicare i criteri. Criteri dei modelli diventano un sistema vincolante che può essere utilizzato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere le proprietà e così via.  
  
 Utilizzando i criteri dei modelli per controllare la visualizzazione di informazioni di **proprietà** finestra è diversa dall'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà dell'oggetto a livello di componente, mentre i criteri dei modelli può essere utilizzato per vincolare le proprietà dell'oggetto a livello di soluzione o progetto. In altre parole  
  
-   Implementare i metodi su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare ciò che viene visualizzato nel **proprietà** finestra per oggetti specifici  
  
-   Utilizzare i criteri dei modelli a livello di soluzione e progetto per determinare ciò che viene visualizzato nel **proprietà** finestra per gli oggetti specificati in precedenza  
  
 Utilizzando i criteri dei modelli per vincolare in modo selettivo le proprietà specifiche nel **proprietà** selezionato nella finestra quando un elemento di progetto di un tipo specificato **Esplora** può essere utile per tutti i membri di il team di sviluppo lavora su un progetto. Utilizza i criteri dei modelli, ad esempio, è possibile impostare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In tal modo, è possibile fornire un modo semplice per garantire che ogni sviluppatore utilizza il percorso corretto per accedere ai dati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)