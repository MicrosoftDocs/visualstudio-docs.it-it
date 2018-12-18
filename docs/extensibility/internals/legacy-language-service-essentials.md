---
title: Funzionalità fondamentali del servizio di linguaggio legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-essentials"></a>Funzionalità fondamentali del servizio di linguaggio legacy
È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio. In questo argomento illustra le funzionalità disponibili in servizi di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Servizi di linguaggio legacy forniscono le funzionalità seguenti:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Colorazione della sintassi|Determina la visualizzazione dell'editor visualizzare diversi colori e stili di carattere per gli elementi di una lingua diversi. Questa distinzione può rendere più facile da leggere e modificare i file.<br /><br /> Per informazioni generali, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità nel framework di pacchetto gestito (MPF), vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Completamento istruzioni|Completa un'istruzione o parola chiave che l'utente ha avviato la digitazione. Completamento delle istruzioni consente agli utenti di immettere istruzioni difficile più facilmente con più rapido e meno probabilità di errore.<br /><br /> Per informazioni generali, vedere [il completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [il completamento delle parole in un servizio di linguaggio Legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Corrispondenza parentesi graffe|Evidenzia i caratteri associati, ad esempio le parentesi graffe. Quando l'utente digita un carattere di chiusura, ad esempio "}", corrispondenza parentesi graffe evidenzia corrispondente carattere, di apertura, ad esempio "{". Quando sono presenti diversi livelli di caratteri di contenimento, questa funzionalità consente agli utenti di confermare che i caratteri di inclusione sono abbinati correttamente.<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [corrispondenza delle parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Descrizioni comandi informazioni di parametro|Visualizza un elenco di possibili firme del metodo di overload che l'utente digita attualmente.<br /><br /> Per informazioni generali, vedere [informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcatori di errore|Viene visualizzata una sottolineatura rossa ondulata, noto anche come un ondulate, sotto il testo che è sintatticamente corretto. Marcatori di errore in genere vengono utilizzati per informare gli utenti delle parole chiave contenente errori di ortografia, le parentesi non chiuse, caratteri non validi ed errori simili.<br /><br /> Nelle classi MPF, i marcatori di errore vengono gestiti automaticamente nel <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|  
  
 Molte di queste funzionalità richiedono il servizio di linguaggio per analizzare il codice sorgente. È spesso possibile riutilizzare la suddivisione in token e l'analisi del codice per il compilatore o un interprete.  
  
 Le funzionalità seguenti sono correlate per il supporto per linguaggi di programmazione, ma non fanno parte dei servizi del linguaggio:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Analizzatori di espressioni|Supporta il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger convalida i punti di interruzione e specificando un elenco di espressioni da visualizzare nel **Auto** finestra di debug.<br /><br /> Per ulteriori informazioni, vedere [supporto per il debug del servizio linguaggio](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Strumenti di esplorazione di simbolo|Supporta **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate**, e **risultati ricerca simbolo**.|