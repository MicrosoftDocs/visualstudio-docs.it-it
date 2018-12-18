---
title: Informazioni rapide in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informazioni rapide in un servizio di linguaggio Legacy
Informazioni rapide di IntelliSense Mostra informazioni su un identificatore dell'origine quando l'utente posiziona il punto di inserimento nell'identificatore di ed è seleziona **informazioni rapide** dal **IntelliSense** menu o mantiene il puntatore del mouse cursore sull'identificatore. In questo modo vengono visualizzati con informazioni sull'identificatore di una descrizione comando. Tali informazioni comprendono in genere il tipo di identificatore. Quando il motore di debug è attivo, queste informazioni possono includere il valore corrente. Il motore di debug fornisce i valori dell'espressione, mentre il servizio di linguaggio gestisce solo gli identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [procedura dettagliata: visualizzazione di descrizioni comandi informazioni rapide](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Le classi del servizio pacchetto gestito (MPF) framework linguaggio forniscono il supporto completo per visualizzare la descrizione comando informazioni rapide di IntelliSense. È necessario effettuare è fornire il testo per visualizzare e abilitare la funzionalità informazioni rapide.  
  
 Il testo da visualizzare viene ottenuto chiamando il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questo motivo indica al parser per ottenere le informazioni sul tipo (o le informazioni appropriate da visualizzare nella descrizione comando informazioni rapide) per l'identificatore nella posizione specificata nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Il <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto è ciò che è stato passato per il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo.  
  
 Il parser deve analizzare tutti gli elementi fino alla posizione nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per determinare i tipi di tutti gli identificatori. Quindi, il parser deve ottenere l'identificatore in corrispondenza della posizione di richiesta di analisi. Infine, il parser deve passare i dati di suggerimento strumento associati a tale identificatore per il <xref:Microsoft.VisualStudio.Package.AuthoringScope> in modo tale oggetto può restituire il testo dell'oggetto di <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> (metodo).  
  
## <a name="enabling-the-quick-info-feature"></a>Abilitazione della funzionalità informazioni rapide  
 Per abilitare la funzionalità informazioni rapide, è necessario impostare il `CodeSense` e `QuickInfo` i parametri denominati del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Impostare questi attributi di <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> e <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> proprietà.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementa la funzionalità informazioni rapide  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione di informazioni rapide di IntelliSense. Quando il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe riceve il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la classe chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (metodo) con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> e il percorso del punto di inserimento al momento il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando è stato inviato. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser metodo è necessario quindi analizzare l'origine nella posizione specificata e quindi analizzare l'identificatore nel percorso specificato per determinare quali elementi visualizzare nella descrizione comando informazioni rapide.  
  
 La maggior parte dei parser non di un'analisi dell'intero file di origine iniziale e archiviare i risultati in una struttura ad albero di analisi. Viene eseguita quando l'analisi completa <xref:Microsoft.VisualStudio.Package.ParseReason> viene passato a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo. Altri tipi di analisi possono quindi utilizzare la struttura ad albero di analisi per ottenere le informazioni desiderate.  
  
 Ad esempio, il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> possibile trovare l'identificatore nel percorso di origine e cercare nell'albero di analisi per ottenere le informazioni sul tipo. Questo tipo di informazioni viene quindi passato al <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe e viene restituito dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodo.