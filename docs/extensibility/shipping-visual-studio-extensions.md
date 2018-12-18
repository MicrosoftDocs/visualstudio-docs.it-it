---
title: Distribuzione di estensioni di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c646ec2c5159e6c3551776761baa9328e3d62bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="shipping-visual-studio-extensions"></a>Distribuzione di estensioni di Visual Studio
Dopo aver completato lo sviluppo dell'estensione, installarlo in altri computer, condividerle con colleghi e amici o pubblicarla in Visual Studio Marketplace. In questa sezione è spiegare tutte le operazioni necessarie per pubblicare e gestire l'estensione: utilizzo di file. VSIX, pubblicazione, localizzazione e l'aggiornamento.  
  
## <a name="working-with-vsix-extensions"></a>Utilizzo di estensioni VSIX  
 È possibile creare un estensioni VSIX creando un progetto VSIX vuoto e quindi aggiungere i modelli di elemento diverso. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
 È possibile utilizzare il formato VSIX per modelli di progetto del pacchetto, l'elemento di componenti di modelli, pacchetti VSPackage, Managed Extensibility Framework (MEF), **della casella degli strumenti** controlli, gli assembly e tipi personalizzati (che include pagine iniziali personalizzate). Il formato VSIX Usa la distribuzione basata su file. Per ulteriori informazioni sui pacchetti VSIX, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Il formato VSIX non supporta l'installazione di frammenti di codice. Non supporta inoltre i alcuni altri scenari quali la scrittura in Global Assembly Cache (GAC) o nel Registro di sistema. Se è necessario scrivere nella Global Assembly Cache o l'installazione del Registro di sistema, è necessario utilizzare il programma di installazione di Windows. Per ulteriori informazioni, vedere [preparazione estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Pubblicare l'estensione di Visual Studio Marketplace  
 È possibile distribuire l'estensione ad altre persone sufficiente mailing tali file. VSIX o inserire in un server. Ma il modo migliore per ottenere il codice in mani di molti utenti viene inserita la [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Sono disponibili agli utenti di Visual Studio tramite le estensioni di Visual Studio Marketplace **estensioni e aggiornamenti**. Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Per un esempio completo che illustra come caricare un'estensione di Visual Studio Marketplace, vedere [procedura dettagliata: pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Durante lo sviluppo di controlli, i modelli e strumenti, è possibile condividerli con l'organizzazione inviando messaggi a una raccolta sulla rete intranet privata. Per altre informazioni, vedere [Private Galleries](../extensibility/private-galleries.md) (Raccolte private).  
  
## <a name="localizing-your-extension"></a>L'estensione di localizzazione  
 Se si prevede di rilasciare l'estensione nelle diverse impostazioni locali, è consigliabile, localizzazione. Per informazioni approfondite, vedere [localizzazione pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>L'aggiornamento e l'estensione di controllo delle versioni  
 Dopo avere pubblicato l'estensione, non esiste, verrà volta quando è necessario aggiornarlo. Per informazioni su come aggiornare un'estensione che è stata pubblicata in Visual Studio Marketplace, vedere [procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 È possibile impostare l'estensione per il supporto di più versioni di Visual Studio. Per ulteriori informazioni, vedere [di supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Viene illustrato come utilizzare il modello di progetto VSIX per installare un modello di progetto personalizzati.|  
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Vengono descritti i componenti di un pacchetto VSIX.|  
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Vengono fornite istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|  
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire testo localizzato per il processo di installazione tramite i file vsixlangpack.|  
|[Procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione del sistema e su come distribuire un aggiornamento a un'estensione di Visual Studio esistente.|  
|[Procedura: Aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere i riferimenti ai pacchetti di distribuzione VSIX.|  
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire un'estensione con Windows Installer.|  
|[Firma di pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Viene illustrato come firmare pacchetti VSIX.|  
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|  
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Viene illustrato come utilizzare il supporto delle estensioni di più versioni di Visual Studio.|
|[Individuazione di Visual Studio](locating-visual-studio.md)|Viene descritto come individuare le istanze di Visual Studio per la distribuzione di un'estensione personalizzata.|
