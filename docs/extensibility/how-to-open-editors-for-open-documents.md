---
title: 'Procedura: aprire gli editor per documenti aperti | Microsoft Docs'
description: Informazioni su come aprire un file in un editor standard o specifico del progetto. Quando un progetto apre una finestra del documento, deve determinare se il file è già aperto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6dfcd44a03b110ae514c2de36092ee07fd0c35e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069920"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: aprire Editor per documenti aperti
Prima di aprire una finestra del documento, il progetto deve innanzitutto determinare se il file è già aperto nella finestra del documento per un altro editor. Il file può essere aperto in un editor specifico del progetto o in uno degli editor standard registrati con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Aprire un editor specifico del progetto
 Utilizzare la procedura seguente per aprire un editor specifico del progetto per un file già aperto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file aperto

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Questa chiamata restituisce i puntatori alla gerarchia del documento, all'elemento della gerarchia e al frame della finestra, se appropriato.

2. Se il documento è aperto, il progetto deve verificare se esiste solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione documento.

   - Se esiste un oggetto visualizzazione del documento e questa visualizzazione è relativa a una gerarchia o a un elemento della gerarchia diverso, il progetto utilizza il puntatore al frame della finestra della visualizzazione per riesporre la finestra esistente.

   - Se esiste un oggetto visualizzazione del documento e questa vista è per la stessa gerarchia e l'elemento della gerarchia, il progetto può aprire una seconda visualizzazione se può collegarsi all'oggetto dati del documento sottostante. In caso contrario, il progetto deve utilizzare il puntatore al frame della finestra della visualizzazione per riesporre la finestra esistente.

   - Se esiste solo l'oggetto dati del documento, il progetto deve determinare se può utilizzare l'oggetto dati del documento per la relativa visualizzazione. Se l'oggetto dati del documento è compatibile, completare la procedura illustrata in [aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

     Se l'oggetto dati del documento non è compatibile, viene visualizzato un errore che indica che il file è attualmente in uso. Questo errore dovrebbe essere visualizzato solo in casi temporanei, ad esempio quando un file viene compilato nello stesso momento in cui l'utente tenta di aprire il file usando un editor diverso dall'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] testo principale. L'editor di testo principale può condividere l'oggetto dati del documento con il compilatore.

3. Se il documento non è aperto perché non è presente alcun oggetto dati documento o oggetto visualizzazione documento, completare i passaggi in [aprire un editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Aprire un editor standard
 Utilizzare la procedura seguente per aprire un editor standard per un file già aperto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard per un file aperto

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Questo metodo verifica innanzitutto che il documento non sia già aperto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Se il documento è già aperto, viene riemersa la finestra dell'editor.

2. Se il documento non è aperto, completare la procedura illustrata in [procedura: aprire gli editor standard](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedi anche
- [Apri e Salva elementi progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: aprire gli editor standard](../extensibility/how-to-open-standard-editors.md)
