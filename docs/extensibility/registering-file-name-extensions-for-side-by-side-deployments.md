---
title: Registrazione di estensioni di File per le distribuzioni Side-By-Side | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae7d7307ef12184dcbfc29254ec5cbae9ff55bb8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrazione di estensioni di File per le distribuzioni Side-By-Side
Per pacchetti VSPackage distribuiti in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file con la versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A meno che non si utilizza un'estensione di file specifici della versione, la registrazione consente agli utenti di aprire il progetto e file di elementi in una versione appropriata di progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Informazioni sulle estensioni di file](../extensibility/about-file-name-extensions.md)  
 Viene descritto come estensioni di file registrate.  
  
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fornisce informazioni su come registrare le applicazioni che possono essere aperti, modifica e così via, un'estensione di file specifico.  
  
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Viene descritto come registrare i verbi.  
  
 [Gestione delle associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)  
 Viene descritto come gestire le installazioni side-by-side in cui una particolare versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamato per aprire un file.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descrive i problemi relativi a più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e ai VSPackage durante lo sviluppo e distribuzione agli utenti finali.