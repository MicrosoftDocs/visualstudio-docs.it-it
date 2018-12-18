---
title: "Supporto di più versioni di Visual Studio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c03df6edc54948060fa3b1f8eee264646a80f38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per pacchetti VSPackage, che significa che un utente può avere più versioni di Visual Studio installate nello stesso computer. Tuttavia, è possibile avere versioni side-by-side di VSPackage caricati in un'unica versione di Visual Studio.  
  
 Prima di eseguire il pacchetto VSPackage può essere caricato in side-by-side versioni di Visual Studio, considerare quanto segue:  
  
-   È necessario determinare la strategia di implementazione side-by-side si desidera seguire.  
  
     Per ulteriori informazioni, vedere [scelta tra condivise e i package VS con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   I formati di file di soluzione e progetto devono essere contenuta la strategia di implementazione.  
  
     Per ulteriori informazioni, vedere [l'aggiornamento dei progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e [la registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Il programma di installazione è necessario gestire la strategia di implementazione in modo che i componenti con controllo delle versioni, nonché i componenti condivisi tra tutte le versioni, correttamente installati e registrati.  
  
     Per ulteriori informazioni, vedere [l'installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) nonché [gestione dei componenti](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installare una versione di Visual Studio installa anche una versione corrispondente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer viene installato anche le versioni 4.0 e 4.5 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], rispettivamente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Scelta tra pacchetti VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Viene descritto come risolvere i problemi di side-by-side in VSPackage.  
  
 [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
