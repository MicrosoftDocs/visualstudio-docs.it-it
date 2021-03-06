---
title: Cenni preliminari sul servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sui servizi di linguaggio legacy in Visual Studio e sulle funzionalità supportate dalle classi del servizio di linguaggio MPF (Managed Package Framework).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 236fc2a2923ffd0829f74ab56a119ff81b29cd7f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061173"
---
# <a name="legacy-language-service-overview"></a>Panoramica dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce supporto per l'editor che consente di implementare determinate [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità. Le classi del servizio di linguaggio MPF (Managed Package Framework) forniscono supporto completo per le funzionalità di uso frequente e il supporto parziale per altre funzionalità.

## <a name="fully-supported-features-in-the-mpf"></a>Funzionalità completamente supportate in MPF
 Le classi del servizio di linguaggio MPF supportano le funzionalità seguenti:

- Evidenziazione della sintassi

- struttura

- Aggiungere commenti a blocchi di codice

- Corrispondenza parentesi graffe

- Frammenti di codice

- Proprietà personalizzate del documento

- Informazioni sui parametri IntelliSense

- Informazioni rapide di IntelliSense

- Completamento del membro IntelliSense

- Completamento parole IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Funzionalità parzialmente supportate in MPF
 MPF fornisce solo il supporto parziale per le funzionalità seguenti. Ciò significa che è necessario implementare i metodi chiamati da MPF.

- Riformattazione del codice. Fornire il codice che implementa la riformattazione.

- Convalida dei punti di interruzione mediante l'identificazione di intervalli di codice validi. Fornire il codice che identifica gli intervalli di codice.

- Supporto della finestra **auto** del debugger per la visualizzazione di variabili. Fornire il codice che determina gli elementi da visualizzare nella finestra.

- Supporto della **barra di navigazione** per la navigazione rapida tra tipi e membri. Implementare e restituire una classe helper che popola gli elenchi nelle caselle combinate della **barra di spostamento** .

## <a name="implementation"></a>Implementazione
 È necessario completare diversi passaggi per implementare il servizio di linguaggio e le funzionalità del servizio di linguaggio che si desidera supportare per la lingua in uso. Questi passaggi sono descritti negli argomenti seguenti:

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Vedi anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)
