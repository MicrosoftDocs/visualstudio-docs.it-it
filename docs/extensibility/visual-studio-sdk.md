---
title: Visual Studio SDK | Microsoft Docs
description: Visual Studio SDK consente di estendere le funzionalità o aggiungere nuove funzionalità a Visual Studio. Informazioni su alcuni dei modi in cui è possibile estendere Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91411ec183e6c51abd825af1080c4330ca46fc90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062525"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK consente di estendere le funzionalità di Visual Studio o di integrare nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti e al Visual Studio Marketplace. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:

- Aggiungere comandi, pulsanti, menu e altri elementi dell'interfaccia utente all'IDE

- Aggiunta di finestre degli strumenti per nuove funzionalità

- Estendi IntelliSense per un determinato linguaggio o fornisci IntelliSense per i nuovi linguaggi di programmazione

- Usare le lampadine per fornire suggerimenti e suggerimenti che consentono agli sviluppatori di scrivere codice migliore

- Abilita supporto per una nuova lingua

- Aggiungere un tipo di progetto personalizzato

- Raggiungi milioni di sviluppatori tramite il Visual Studio Marketplace

  Se non è mai stata scritta un'estensione di Visual Studio, è necessario trovare altre informazioni su queste funzionalità e [avviare lo sviluppo di estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installare Visual Studio SDK
 Visual Studio SDK è una funzionalità facoltativa del programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Novità di Visual Studio SDK
 Visual Studio SDK include alcune nuove funzionalità, ad esempio il formato di avviso di estensioni autocaricate in modo sincrono e VSIX V3, nonché le modifiche di rilievo, che possono richiedere l'aggiornamento dell'estensione. Per ulteriori informazioni, vedere Novità di [Visual studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md) e novità [di Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Linee guida sull'esperienza utente di Visual Studio
 Suggerimenti utili per la progettazione dell'interfaccia utente per l'estensione nelle [linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 È anche possibile ottenere informazioni su come fare in modo che l'estensione abbia un aspetto notevole nei dispositivi ad alta risoluzione con i [problemi di indirizzo dpi](../extensibility/addressing-dpi-issues2.md) .

 Sfrutta i vantaggi del [servizio immagini e del catalogo](../extensibility/image-service-and-catalog.md) per ottimizzare la gestione delle immagini e il supporto per valori dpi e temi elevati.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Trovare e installare le estensioni di Visual Studio esistenti
 È possibile trovare le estensioni di Visual Studio nella finestra di dialogo **estensioni e aggiornamenti** del menu **strumenti** . Per altre informazioni, vedere [trovare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). È anche possibile trovare estensioni nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Riferimenti per Visual Studio SDK
 Informazioni di riferimento sulle API di Visual Studio SDK sono disponibili in [riferimenti a Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK
 È possibile trovare esempi Open Source di estensioni di Visual Studio SDK in GitHub in [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Questo repository GitHub contiene esempi che illustrano varie funzionalità estendibili in Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK
 In caso di domande su VSSDK o se si vuole condividere le proprie esperienze sviluppando estensioni, è possibile usare il [Forum di estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o la [chat di ExtendVS](https://gitter.im/Microsoft/extendvs).

 Per ulteriori informazioni, vedere il [Blog di VSX Arcana](/archive/blogs/vsx/) e diversi blog scritti da Microsoft MVP:

- [Estensioni di Visual Studio preferite](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Estendibilità in Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Estensione di Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Vedi anche

- [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Domande frequenti: conversione di componenti aggiuntivi in estensioni VSPackage](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Gestire più thread nel codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Estendi menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Aggiungere comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)
- [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor e estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md)
- [Estendi progetti](../extensibility/extending-projects.md)
- [Estendi impostazioni utente e opzioni](../extensibility/extending-user-settings-and-options.md)
- [Creare modelli di progetto e di elemento personalizzati](../extensibility/creating-custom-project-and-item-templates.md)
- [Estendi proprietà e finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md)
- [Estendi altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Usare e fornire servizi](../extensibility/using-and-providing-services.md)
- [Gestire VSPackage](../extensibility/managing-vspackages.md)
- [Shell isolata di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Distribuire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Riferimenti per Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)