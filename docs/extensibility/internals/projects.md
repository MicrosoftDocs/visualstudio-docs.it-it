---
title: Progetti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2ca4edabcee9f561dea51ea4b579ce194d13fa8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="projects"></a>Progetti
In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare i file del codice sorgente e altre risorse che vengono visualizzati in **Esplora**. In genere, i progetti sono file (ad esempio, un file con estensione csproj per un progetto c#) che archiviano i riferimenti ai file del codice sorgente e alle risorse come file bitmap. Progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a servizi Web e database e altre risorse. Pacchetti VSPackage possono estendere il sistema del progetto di Visual Studio in tre modi principali: *tipi di progetto*, *sottotipi di progetto*, e *strumenti personalizzati*.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 *I tipi di progetto* aggiungere il supporto per nuovi tipi di progetti, ad esempio linguaggi di programmazione. Ad esempio, ogni linguaggio che supporta Visual Studio ha un proprio tipo di progetto e l'esempio di integrazione di IronPython include un tipo di progetto per la lingua di IronPython. È necessario creare un tipo di progetto per linguaggi diversi da c# o Visual Basic per personalizzare come elementi sono compilati, eseguire il debug, distribuiti e visualizzati in **Esplora**. Per ulteriori informazioni, vedere [tipi di progetto](../../extensibility/internals/project-types.md).  
  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 *Sottotipi di progetto* sono basati sui tipi di progetto e può essere utilizzato per personalizzare il modo in cui progetti vengono compilati, il debug e distribuire. Visual Studio Usa sottotipi di progetto con progetti Smart Device. la personalizzazione di distribuzione tramite la copia di un programma appena compilato da un computer di sviluppo nel dispositivo di destinazione. Tipi di progetto Visual Basic e c# possono essere utilizzati come base per i sottotipi di progetto; Tipi di progetto C++ non è possibile. I tipi di progetto anche utilizzabile come base per i sottotipi di progetto. Per ulteriori informazioni, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
 [Progetti Web](../../extensibility/internals/web-projects.md)  
 Viene illustrato il progetto Web, che consentono di creare applicazioni Web.  
  
 [Nuova generazione del progetto: Dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione progetto: dietro le quinte, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Viene illustrato ciò che effettivamente si verifica quando si crea un nuovo progetto.  
  
 [Esempi di VSSDK](http://aka.ms/vs2015sdksamples)  
 Contiene gli esempi relativi progetti e soluzioni in Visual Studio SDK.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Componenti e funzionalità di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Illustrano diversi aspetti di estendibilità di Visual Studio.