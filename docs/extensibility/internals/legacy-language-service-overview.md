---
title: Cenni preliminari sul servizio di linguaggio legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8641a3e009cb5a7b61d8334b6dcb2440d186f4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-overview"></a>Cenni preliminari sul servizio di linguaggio legacy
Un servizio di linguaggio fornisce il supporto di editor che consente di implementare determinati [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità. Le classi del servizio di linguaggio del file system distribuito (MPF, Managed Package Framework) forniscono il supporto completo per le funzionalità di frequente e supporto parziale per altre funzionalità.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Funzionalità completamente supportate in MPF  
 Le classi del servizio di linguaggio MPF supportano le funzionalità seguenti:  
  
-   Evidenziazione della sintassi  
  
-   struttura  
  
-   Blocchi di commenti di codice  
  
-   Corrispondenza parentesi graffe  
  
-   Frammenti di codice  
  
-   Proprietà personalizzate del documento  
  
-   Informazioni sui parametri di IntelliSense  
  
-   Informazioni rapide di IntelliSense  
  
-   Completamento di IntelliSense membro  
  
-   Completa parola di IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Funzionalità parzialmente supportate in MPF  
 Il Framework MPF supporta solo parzialmente per le funzionalità seguenti. Ciò significa che è necessario implementare i metodi che vengono chiamati dal MPF.  
  
-   La formattazione di codice. Specificare il codice che implementa la riformattazione.  
  
-   Convalida i punti di interruzione identificando gli intervalli di codice valido. Specificare il codice che identifica le estensioni di codice.  
  
-   Supporto del debugger **Auto** finestra per la visualizzazione delle variabili. Specificare il codice che determina gli elementi da visualizzare nella finestra.  
  
-   Supporto di **barra di spostamento** per la navigazione rapida tra i tipi e membri. Implementare e restituire una classe helper che consente di popolare gli elenchi presenti nel **barra di spostamento** caselle combinate.  
  
## <a name="implementation"></a>Implementazione  
 È necessario completare diversi passaggi per implementare il servizio di linguaggio stesso e le funzionalità del linguaggio che si desidera supportare per la propria lingua. I singoli passaggi sono descritti negli argomenti seguenti:  
  
-   [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Definizione della struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)