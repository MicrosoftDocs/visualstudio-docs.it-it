---
title: Creazione di tipi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1ab4f9f41fc2e98fcc9b2f7a9aeec6885e3b3005
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-types"></a>Creazione di tipi di progetto
È possibile estendere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creando un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere alcuni concetti e completare una serie di passaggi. Gli argomenti seguenti forniscono una panoramica di come creare tipi di progetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Decisioni di progettazione relative al tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)  
 Viene illustrato l'elemento, la persistenza del file di progetto e impegno meccanico sulle scelte di progettazione è necessario apportare prima di creare un nuovo tipo di progetto.  
  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Viene fornita una panoramica dei passaggi che è necessario seguire per creare un nuovo tipo di progetto che supporta attività di programmazione come la modifica del codice e la compilazione, compilazione, debug e distribuzione di applicazioni nel progetto.  
  
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fornisce informazioni su come specificare e utilizzare una factory del progetto per creare istanze di un nuovo progetto.  
  
 [Registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)  
 Vengono forniti esempi di codice di istruzioni dal Registro di sistema che forniscono dati e i percorsi predefiniti e una tabella che contengono le voci dello script del Registro di sistema per ogni istruzione.  
  
 [Salvataggio permanente dei progetti](../../extensibility/internals/project-persistence.md)  
 Viene illustrato l'utilizzo di `IPersistFileFormat` per rendere persistenti i file e gli oggetti non basate su file di progetto.  
  
 [Uso di MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descrive come è possibile utilizzare il tipo di progetto di [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] per consentire agli utenti di compilare dal motore di compilazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e nella riga di comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Viene illustrata l'architettura di strumenti per la visualizzazione, ad esempio di codice il **Visualizzatore oggetti** e **Visualizzazione classi** finestra. Descrive le interfacce e metodi utilizzati per implementare l'esplorazione oggetti in un pacchetto VSPackage.  
  
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Illustra l'importanza che svolgono progetti per determinare quale editor viene utilizzato quando si apre un elemento di progetto e come risorse di progetto possono essere modificate.  
  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Viene illustrato come assegnare la propria identità univoca di VSPackage e come eseguire il wrapping delle DLL VSPackage e altre informazioni in un pacchetto Windows Installer (. File con estensione MSI) per la distribuzione ai clienti.  
  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie viste e gli indirizzi.  
  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)  
 Viene fornita una panoramica di un VSPackage, un oggetto COM installabile che estende il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e viene illustrato come implementare il propria VSPackage.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene illustrato come utilizzare i progetti per modificare il codice, compilare e codice, compilare ed eseguire e il debug del codice e vengono forniti collegamenti ad argomenti dettagliati su come creare tipi di progetto.