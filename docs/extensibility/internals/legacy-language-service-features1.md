---
title: Linguaggio legacy servizio Features1 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-features"></a>Funzionalità del linguaggio legacy
Un servizio di linguaggio di pacchetto gestito (MPF) framework può supportare uno o più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità, ad esempio l'evidenziazione della sintassi, IntelliSense e convalida del punto di interruzione. Ogni funzionalità può essere implementata indipendente dagli altri, ma tutti richiedono un parser e uno scanner, ad eccezione di evidenziazione della sintassi, che richiede solo uno scanner.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare la coppia di lingue corrispondenti, noto anche come corrispondenza parentesi graffe.  
  
 [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare l'aggiunta di commenti e rimuovendo di codice selezionato.  
  
 [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare le proprietà di documento che sono incorporate in un file di origine.  
  
 [Definizione della struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare la struttura tramite l'implementazione di aree nascoste.  
  
 [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare riformattando codice.  
  
 [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare i frammenti di codice, ovvero i segmenti di codice che vengono inseriti e possono essere modificati.  
  
 [Informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Vengono descritte le funzionalità necessarie per supportare l'operazione di informazioni sul parametro di IntelliSense per la visualizzazione di una firma del metodo come il metodo è tipizzato.  
  
 [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare l'operazione di informazioni rapide di IntelliSense per visualizzare informazioni su un identificatore.  
  
 [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Viene descritto cosa è necessario per supportare l'operazione di completamento IntelliSense membro per la selezione di un membro di uno spazio dei nomi da un elenco.  
  
 [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare l'operazione completa parola di IntelliSense per il completamento di parole parzialmente tipizzate.  
  
 [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Viene descritto ciò che è possibile eseguire un servizio di linguaggio per supportare il **Auto** finestra durante il debug.  
  
 [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Viene descritto come utilizzare il **barra di spostamento** nella parte superiore della visualizzazione dell'editor per fornire la navigazione rapida per qualsiasi tipo o membro nel file da visualizzare...  
  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Vengono descritte le funzionalità necessarie per supportare l'evidenziazione della sintassi del codice sorgente.  
  
 [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Viene descritto ciò che è possibile eseguire un servizio di linguaggio per supportare la convalida dei punti di interruzione all'esterno di un debugger.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Viene descritto il parser e scanner necessari per implementare tutte le funzionalità di un servizio di linguaggio che utilizza il framework di pacchetto gestito.  
  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Vengono descritte le funzionalità necessarie per implementare un servizio di linguaggio tramite MPF.  
  
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Vengono descritti i passaggi necessari per registrare un servizio di linguaggio basato su MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)  
 Viene illustrato come IntelliSense rende facilmente accessibili i riferimenti del linguaggio.  
  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Fornisce informazioni su come utilizzare il framework di pacchetto gestito (MPF) per implementare un servizio di linguaggio completo nel codice gestito.