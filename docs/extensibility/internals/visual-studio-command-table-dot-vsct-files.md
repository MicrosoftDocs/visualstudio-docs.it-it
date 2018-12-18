---
title: Visual Studio Command Table (. File Vsct) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Command Table (. File Vsct)
Un file di configurazione di tabella comandi è un file di testo che descrive il set di comandi che contiene un pacchetto VSPackage. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando compilatore tabella (VSCT) compila il file di configurazione basato su XML (file con estensione vsct) in file di output (CTO) nella tabella di comando binary. I file CTO risultanti sono gli stessi di quelli che vengono creati utilizzando il compilatore di tabella (CTC) del comando per compilare i file di configurazione CTC. Tuttavia, il file vsct basato su XML presenta alcuni vantaggi, ad esempio un editor XML e IntelliSense XML.  
  
 Per ulteriori informazioni sulla sintassi e semantica dei file con estensione vsct, vedere [Progettazione tabella comandi XML (. File Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>In questa sezione  
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Viene descritto come progettare i file con estensione vsct.  
  
 [Procedura: Creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Confronta i metodi per la creazione di un file con estensione vsct. Descrive il processo per la creazione manuale di un nuovo file con estensione vsct.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML nella tabella di comando.  
  
 [Comando tabella configurazione (. File CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Viene presentata una panoramica del formato di file CTC deprecate.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descrive la specifica di formato di tabella comandi.  
  
 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Viene descritto come utilizzare le risorse gestite e in pacchetti VSPackage gestiti.  
  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.