---
title: Sviluppo di un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cf384a22429c6314bf5e2fcbb66db7974d42c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="developing-a-legacy-language-service"></a>Sviluppo di un servizio di linguaggio Legacy
Questa sezione sono riportati i collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul programma per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornisce un modello di servizio di linguaggio minimo per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale. È possibile utilizzare questo modello come guida per la creazione di un proprio servizio di linguaggio.  
  
 [Interfacce dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e fornisce un elenco di oggetti aggiuntivi che è possibile utilizzare per fornire evidenziazione della sintassi, i dati di metodo e altre funzionalità.  
  
 [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Viene descritto come inserire un filtro al servizio di linguaggio per i comandi intercetta gestire in altro modo la visualizzazione del testo.  
  
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fornisce informazioni su come registrare il servizio di linguaggio tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.  
  
 [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor di componenti di base.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Viene illustrato come implementare l'evidenziazione della sintassi del servizio di linguaggio.  
  
 [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Illustra il completamento, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento avviate digitando.  
  
 [Informazioni sul parametro in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Viene descritto come fornire suggerimenti di metodo per i metodi e le funzioni in overload.  
  
 [Procedura: Fornire il supporto per il testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Viene illustrato lo scopo di un'area di testo nascosto e vengono fornite istruzioni su come implementare un'area di testo nascosto.  
  
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Vengono descritte le due opzioni che estendono il supporto della struttura per il linguaggio oltre, supportando il *Comprimi alle definizioni* comando.