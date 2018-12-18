---
title: Contesto del progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 99f073e7f27fc98c1c751ae8153adfeea0018e2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-context"></a>Contesto del progetto
Quando l'utente aggiunge o funziona con i progetti ed elementi di progetto, l'IDE Usa il concetto di contesto del progetto per determinare come le varie operazioni devono essere eseguite.  
  
 In genere, i file sono gli oggetti di progetto standard creati dall'utente in modo esplicito selezionando il **nuovo progetto** comando o messo a disposizione selezionando il **Apri progetto** comando il  **File** menu. In questi casi, i file vengono creati e aperto nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.  
  
 Alcuni progetti forniscono un contesto molto dettagliato. Ad esempio, il progetto gestisce un spazio dei nomi con ambito di progetto a livello di codice o una connessione con ambito di progetto di database per l'associazione dati. L'utente può spesso aprire file o le connessioni al database direttamente tramite un oggetto di progetto specifico, ad esempio un elemento di progetto visualizzato in Esplora soluzioni.  
  
 In altri casi, il contesto dell'elemento non viene specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il **aprire i File esistenti** comando il **File** menu quando il debugger viene eseguito su un file, o quando l'utente fa clic il **Cerca nei file** comando il **Trova e sostituisci** la finestra di dialogo. Per gestire queste situazioni, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di individuazione il progetto migliore per aprire un documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Priorità del progetto](../../extensibility/internals/project-priority.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)