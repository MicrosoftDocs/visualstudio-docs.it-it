---
title: Architettura di tipi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34402ae0b998d4ae534507e23ffa31e0d7cef9bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-types-architecture"></a>Architettura di tipi di progetto
In questa sezione contiene informazioni dettagliate sull'architettura dei tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)  
 Elenca i servizi che può utilizzare un tipo di progetto e le interfacce che deve implementare.  
  
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)  
 Descrive le interfacce, tipi di progetto devono implementare sia possono implementare facoltativamente per fornire funzionalità aggiuntive.  
  
 [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)  
 Consente di decidere quando è necessario creare un progetto di tipo e quando si utilizza un altro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità di estendibilità, ad esempio un editor e pacchetti VSPackage per ottenere lo stesso obiettivo.  
  
 [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)  
 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza gerarchie e il contesto di selezione per fornire un'esperienza utente semplice e coerente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 Viene illustrato come sottotipi di progetto consentono di personalizzare il comportamento dei sistemi di progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Fornisce una panoramica dei progetti come blocchi predefiniti di base di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.