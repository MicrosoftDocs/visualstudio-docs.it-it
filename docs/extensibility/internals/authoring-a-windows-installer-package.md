---
title: Creazione di un pacchetto di Windows Installer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2055f57e78c348f3f8e53187126588f382f0b944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-a-windows-installer-package"></a>Creazione di un pacchetto di Windows Installer
Unità di dati del modello di Windows Installer. Invece che scrivere uno script contenente le procedure per copiare i file e la scrittura di voci del Registro di sistema, ad esempio, si creano le righe e colonne nelle tabelle di database che contengono dati di file e Registro di sistema.  
  
## <a name="database-entries"></a>Voci di database  
 Per installare un pacchetto VSPackage, un pacchetto Windows Installer deve contenere le voci di database per eseguire le attività seguenti:  
  
-   Ricerca per individuare le versioni di sistema [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage supporta (tramite le tabelle di Windows Installer che includono AppSearch, CompLocator, RegLocator, DrLocator e firma).  
  
-   Annullare l'installazione, se nessuna versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installato o se un altro requisito di sistema del VSPackage non viene soddisfatta (utilizzando la tabella LaunchCondition).  
  
-   Installare il pacchetto VSPackage e i file dipendenti (tramite la directory, il componente e le tabelle file).  
  
-   Aggiungere le informazioni appropriate per il pacchetto VSPackage nel Registro di sistema (utilizzando la tabella del Registro di sistema).  
  
-   Integrare il VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamando **devenv.exe /setup** (utilizzando la tabella CustomAction).  
  
 Per ulteriori informazioni, vedere [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Strumenti di installazione  
 Un'ampia gamma di strumenti di installazione di terze parti offrono un ambiente di sviluppo per pacchetti Windows Installer. Due strumenti gratuiti sono i seguenti:  
  
-   InstallShield Limited Edition  
  
     È possibile ottenere una versione limitata di InstallShield tramite Visual Studio **nuovo progetto** finestra di dialogo. Espandere **altri tipi di progetto** e quindi selezionare **installazione e distribuzione**. Selezionare il modello di InstallShield.  
  
-   set di strumenti XML di Windows Installer  
  
     Il set di strumenti consente di compilare pacchetti di Windows Installer dai file di origine XML. Il set di strumenti è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e i file eseguibili da [http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix).  
  
 Per i prodotti che si integrano in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vedere [http://visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)