---
title: Le estensioni del servizio dell'editor e della lingua | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 59de764dfcb976dfac303f44a67340e117ae5e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="editor-and-language-service-extensions"></a>Editor e le estensioni del servizio di linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio. L'editor è basato su Windows Presentation Foundation (WPF) e viene scritto in codice gestito. Sebbene questa struttura è diverso dal progettazioni nelle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, usare Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK fornisce adapter noto come *shim* per supportare i pacchetti VSPackage che sono state scritte per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere l'affidabilità e prestazioni migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'utilizzo di modelli di elemento di Editor.|  
|[Estensione dell'editor e dei servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti a documenti che presentano le funzionalità dell'editor di componenti di base e la progettazione e viene illustrato come l'estensione.|  
|[Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Collegamenti a documenti che descrivono come accedere all'editor di componenti di base da codice esistente.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti a documenti che descrivono come creare editor personalizzati.|  
|[Estendibilità dei servizi di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti a documenti che descrivono come integrare i linguaggi di programmazione in Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Introduce Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Viene introdotto Windows Presentation Foundation (WPF).|