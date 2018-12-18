---
title: Contesto del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-context"></a>Contesto del progetto
Quando l'utente aggiunge o funziona con i progetti ed elementi di progetto, l'IDE Usa il concetto di contesto del progetto per determinare come le varie operazioni devono essere eseguite.  
  
 In genere, i file sono gli oggetti di progetto standard creati dall'utente in modo esplicito selezionando il **nuovo progetto** comando o messo a disposizione selezionando il **Apri progetto** comando il  **File** menu. In questi casi, i file vengono creati e aperto nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.  
  
 Alcuni progetti forniscono un contesto molto dettagliato. Ad esempio, il progetto gestisce un spazio dei nomi con ambito di progetto a livello di codice o una connessione con ambito di progetto di database per l'associazione dati. L'utente può spesso aprire file o le connessioni al database direttamente tramite un oggetto di progetto specifico, ad esempio un elemento di progetto visualizzato in Esplora soluzioni.  
  
 In altri casi, il contesto dell'elemento non viene specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il **aprire i File esistenti** comando il **File** menu quando il debugger viene eseguito su un file, o quando l'utente fa clic il **Cerca nei file** comando il **Trova e sostituisci** la finestra di dialogo. Per gestire queste situazioni, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di individuazione il progetto migliore per aprire un documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Priorità del progetto](../../extensibility/internals/project-priority.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)