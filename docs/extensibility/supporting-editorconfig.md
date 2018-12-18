---
title: Estensione di un servizio di linguaggio per il supporto di EditorConfig in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2aa80903b3e5ea2723ec576fa463161b8d003c93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Supporto EditorConfig per il servizio di linguaggio

[EditorConfig](http://editorconfig.org/) file consentono di descrivere opzioni dell'editor di testo comuni, ad esempio Dimensione rientro, in base al progetto. Per ulteriori informazioni sul supporto di Visual Studio per i file EditorConfig, vedere [creare le impostazioni di editor portabile utilizzando EditorConfig](../ide/create-portable-custom-editor-options.md).

Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Per le modifiche, ad esempio tabulazioni e spazi, tuttavia, alcuni servizi di linguaggio scegliere di utilizzare un'opzione di visualizzazione testo contestuali appropriato, anziché utilizzare le impostazioni globali. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Di seguito sono le modifiche necessarie per aggiornare un servizio di linguaggio per il supporto di file EditorConfig, sostituendo globale _specifici della lingua_ con un _contestuali_ opzione:

## <a name="indent-style"></a>Stile rientro

Opzioni specifiche del linguaggio | Opzioni di scelta rapida
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Dimensione rientro

Opzioni specifiche del linguaggio | Opzioni di scelta rapida
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Dimensione tabulazione

Opzioni specifiche del linguaggio | Opzioni di scelta rapida
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Vedere anche

[Creare le impostazioni di editor portabile usando EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Estendere i servizi di editor e della lingua](../extensibility/extending-the-editor-and-language-services.md)