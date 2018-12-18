---
title: Novità&#39;s New in Visual Studio 2017 SDK | Documenti Microsoft
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abc1f12a5a6c7368bc47e8f4e924d109dcf87f57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novità&#39;s New in Visual Studio 2017 SDK

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato v3 VSIX

Per supportare la nuova installazione leggero di Visual Studio 2017, il formato del manifesto VSIX estensione è stato aggiornato alla versione 3 (v3 VSIX).

Il nuovo formato dispone del supporto per:

* Consente di dichiarare in modo esplicito i prerequisiti per essere rilevati e installati per il VSIXInstaller.
* Assembly Ngen sull'installazione dell'estensione.
* L'installazione di asset esterna alla radice di estensione normali.

Per ulteriori informazioni su queste modifiche, vedere gli argomenti seguenti:

* [Modifiche apportate all'estendibilità per 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Installazione all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti per l'estensibilità di Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>La migrazione di progetto di estendibilità di Visual Studio 2017

Per informazioni su come aggiornare i progetti di estendibilità e i relativi manifesti VSIX per Visual Studio 2017, vedere [procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelli di progetto e di elemento personalizzati

A partire da Visual Studio 2017, l'analisi per un progetto personalizzato e modelli di elementi verrà non verrà eseguita. Al contrario, l'estensione è necessario fornire file manifesto che descrivono il percorso di installazione di questi modelli. Per aggiornare le estensioni VSIX, è possibile utilizzare Visual Studio 2017. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere [aggiornamento progetto personalizzato e i modelli di Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schema del modello di manifesto è documentato [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Linee guida sulle prestazioni di estensione aggiornata

È disponibile un nuovo [procedura: diagnosticare le prestazioni di estensione](how-to-diagnose-extension-performance.md) argomento nella sezione [gestione VSPackage](managing-vspackages.md) per mostrare come rilevare e analizzare l'impatto di estensione in Visual Studio avvio e soluzione tempi di caricamento.
