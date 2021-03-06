---
title: Servizio di linguaggio legacy Features2 | Microsoft Docs
description: Informazioni su alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire usando le estensioni Managed Extensibility Framework (MEF) in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a12ee207f7fb7e4f4e2d202d5d63d468e9cea547
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074483"
---
# <a name="legacy-language-service-features-2"></a>Funzionalità del servizio di linguaggio Legacy 2
Negli argomenti seguenti sono elencate alcune delle funzionalità del servizio di linguaggio legacy che è possibile fornire.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare la colorazione della sintassi.

- [Formattazione automatica in un servizio di linguaggio legacy](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Viene illustrato come implementare la formattazione automatica.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene illustrato come implementare la descrizione comando informazioni parametri IntelliSense.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'elenco di istruzioni IntelliSense e l'elenco di completamento dei membri.

- [Definizione della struttura e testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Viene illustrato come implementare la struttura o il testo nascosto.

- [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrati alcuni passaggi nell'implementazione del supporto del debugger.

## <a name="related-sections"></a>Sezioni correlate
