---
title: Distribuzione delle estensioni di Visual Studio | Microsoft Docs
description: Informazioni su come pubblicare e gestire l'estensione di Visual Studio SDK, tra cui l'uso di file con estensione VSIX, la pubblicazione, la localizzazione e l'aggiornamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c88c80ffbc1e80815b8370a940a75c0eb197ff78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090135"
---
# <a name="shipping-visual-studio-extensions"></a>Distribuzione delle estensioni di Visual Studio
Dopo aver completato lo sviluppo dell'estensione, è possibile installarla in altri computer, condividerla con gli amici e i colleghi oppure pubblicarla nel Visual Studio Marketplace. In questa sezione vengono illustrate tutte le operazioni che è necessario eseguire per pubblicare e gestire l'estensione: uso dei file VSIX, pubblicazione, localizzazione e aggiornamento.

## <a name="working-with-vsix-extensions"></a>Uso delle estensioni VSIX
 È possibile creare estensioni VSIX creando un progetto VSIX vuoto e quindi aggiungendovi modelli di elementi diversi. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

 È possibile usare il formato VSIX per creare pacchetti di modelli di progetto, modelli di elemento, VSPackage, componenti Managed Extensibility Framework (MEF), controlli della **casella degli strumenti** , assembly e tipi personalizzati (incluse le pagine iniziali personalizzate per Visual Studio 2017). Il formato VSIX usa la distribuzione basata su file. Per altre informazioni sui pacchetti VSIX, vedere [anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Il formato VSIX non supporta l'installazione dei frammenti di codice. Non supporta inoltre altri scenari, ad esempio la scrittura nella global assembly cache (GAC) o nel registro di sistema. Se è necessario scrivere nella GAC o nel registro di sistema nell'installazione di, è necessario utilizzare il Windows Installer. Per ulteriori informazioni, vedere [preparazione delle estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Pubblicazione dell'estensione nel Visual Studio Marketplace
 È possibile distribuire l'estensione ad altre persone semplicemente inviando il file con estensione VSIX o inserendolo in un server. Tuttavia, il modo migliore per ottenere il codice per la maggior parte delle persone consiste nell'inserirlo nella [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Visual Studio Marketplace estensioni sono disponibili per gli utenti di Visual Studio tramite **estensioni e aggiornamenti**. Per altre informazioni, vedere [ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Per un esempio completo in cui viene illustrato come caricare un'estensione nel Visual Studio Marketplace, vedere [procedura dettagliata: pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Quando si sviluppano controlli, modelli e strumenti, è possibile condividerli con l'organizzazione inserendoli in una raccolta privata sulla Intranet. Per altre informazioni, vedere [raccolte private](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localizzazione dell'estensione
 Se si prevede di rilasciare l'estensione in impostazioni locali diverse, è necessario prenderne in considerazione la localizzazione. Per una spiegazione degli elementi necessari, vedere [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aggiornamento e controllo delle versioni dell'estensione
 Dopo aver pubblicato l'estensione, sarà necessario eseguire l'aggiornamento in un momento specifico. Per informazioni su come aggiornare un'estensione pubblicata nel Visual Studio Marketplace, vedere [procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md).

 È possibile impostare l'estensione in modo da supportare più versioni di Visual Studio. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Viene illustrato come usare il modello di progetto VSIX per installare un modello di progetto personalizzato.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive i componenti di un pacchetto VSIX.|
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Vengono fornite istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire il testo localizzato per il processo di installazione utilizzando i file con estensione vsixlangpack.|
|[Procedura: Aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione nel sistema e come distribuire un aggiornamento a un'estensione di Visual Studio esistente.|
|[Procedura: Aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere riferimenti ai pacchetti di distribuzione VSIX.|
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire l'estensione con Windows Installer.|
|[Firma di pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Viene illustrato come firmare i pacchetti VSIX.|
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Viene illustrato come fare in modo che l'estensione supporti più versioni di Visual Studio.|
|[Individuazione di Visual Studio](locating-visual-studio.md)|Viene descritto come individuare le istanze di Visual Studio per la distribuzione di estensioni personalizzate.|
