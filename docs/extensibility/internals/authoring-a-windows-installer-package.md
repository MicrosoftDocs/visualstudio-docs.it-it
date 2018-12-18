---
title: Creazione di un pacchetto di Windows Installer | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 215e1496d35059448cf11457658b7d1270b5677d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
  
     Il set di strumenti consente di compilare pacchetti di Windows Installer dai file di origine XML. Il set di strumenti è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e i file eseguibili da [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Per i prodotti commerciali integrano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vedere [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)