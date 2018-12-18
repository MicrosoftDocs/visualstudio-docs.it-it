---
title: Le interfacce legacy nell'Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64e867430c2ae55f530bdb66844240a887bd5545
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfacce legacy nell'Editor
Editor di Visual Studio è possibile accedere da interfacce legacy. Visual Studio SDK include schede di rete come *shim*, che consentono di queste interfacce interagire con il nuovo editor. Tuttavia, è consigliabile aggiornare il codice legacy per utilizzare il nuovo editor di API. Il codice garantiscono prestazioni migliori ed è possibile usare nuove tecnologie, ad esempio Windows Presentation Foundation (WPF) e Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Adattamento del codice Legacy nell'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Viene illustrato come adattare il codice per il nuovo editor.|  
|[Comportamento nuovo o modificato con schede dell'Editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Viene illustrato come il comportamento delle schede dell'editor è diverso da quello delle precedenti versioni dell'editor.|  
|[Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)|Descrive i diversi componenti di versioni precedenti dell'editor.|  
|[Creazione di istanze di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Viene illustrato come utilizzare l'API legacy per creare un'istanza di editor di componenti di base.|  
|[Factory editor](../extensibility/editor-factories.md)|Viene illustrato come utilizzare il factory editor con l'API legacy.|  
|[Procedura: registrare i tipi di File dell'Editor](../extensibility/how-to-register-editor-file-types.md)|Viene descritto come collegare un'estensione di file nell'editor.|  
|[Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Viene illustrato come creare un core editor e collegare un'estensione di file.|  
|[Procedura: fornire contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)|Viene illustrato come fornire contesto per l'editor.|  
|[Servizi per linguaggi e l'Editor di componenti di base](../extensibility/language-services-and-the-core-editor.md)|Illustra le interazioni tra un servizio di linguaggio e un editor.|  
|[Accesso ai Buffer di testo tramite l'API Legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Viene illustrato come accedere al buffer di testo tramite l'API legacy.|  
|[L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Viene illustrato come accedere alla visualizzazione di testo tramite l'API legacy.|  
|[Personalizzazione di codice Windows tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Viene descritto come personalizzare finestre del codice tramite l'API legacy.|  
|[L'accesso ai livelli di testo tramite l'API Legacy](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Viene illustrato come accedere a diversi livelli di testo con l'API legacy.|  
|[Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)|Viene illustrato come aggiungere marcatori di testo tramite l'API legacy.|  
|[Personalizzazione di menu e controlli di Editor utilizzando l'API Legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Viene illustrato come personalizzare i controlli di editor utilizzando l'API legacy.|  
|[Annullamento di gestione e il ripristino tramite l'API Legacy](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Viene illustrato come gestire l'annullamento e ripetizione tramite l'API legacy.|  
|[Procedura: implementare Trova e Sostituisci meccanismo](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Viene illustrato come gestire Trova e Sostituisci tramite l'API legacy.|  
|[Procedura: eliminare le notifiche di modifica File](../extensibility/how-to-suppress-file-change-notifications.md)|Viene illustrato come escludere le notifiche di modifica di file tramite l'API legacy.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Viene illustrato come creare editor personalizzati.|  
|[Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)|Vengono forniti collegamenti a documenti sulle funzionalità che forniscono funzionalità di personalizzazione per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale aggiungendo supporto per un servizio di linguaggio.|  
|[Utilizzo di tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)|Viene illustrato come utilizzare i tipi di carattere e colori con le interfacce legacy.|