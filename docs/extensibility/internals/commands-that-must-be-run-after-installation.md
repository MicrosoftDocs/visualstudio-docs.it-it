---
title: I comandi che devono essere eseguiti dopo l'installazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84f1651f311fbad7aefe40a2744c61dc7d81725c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandi che devono essere eseguiti dopo l'installazione
Se si distribuisce l'estensione tramite un file con estensione msi, è necessario eseguire `devenv /setup` come parte dell'installazione nell'ordine per Visual Studio individuare le estensioni.  
  
> [!NOTE]
>  Le informazioni contenute in questo argomento si applicano a ricerca di DevEnv con Visual Studio 2008 e versioni precedenti. Per informazioni su come individuare DevEnv con le versioni successive di Visual Studio, vedere [requisiti di sistema di rilevamento](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Trovare devenv.exe  
 È possibile individuare ogni versione devenv.exe dal Registro di sistema valori [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] scrivere programmi di installazione, utilizzando la tabella RegLocator e la tabella AppSearch per archiviare i valori del Registro di sistema come proprietà. Per ulteriori informazioni, vedere [requisiti di sistema di rilevamento](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Righe della tabella RegLocator individuare devenv.exe da diverse versioni di Visual Studio  
  
|Signature_|radice|Chiave|nome|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Righe della tabella AppSearch per le righe di tabella RegLocator corrispondente  
  
|Proprietà|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Ad esempio, il programma di installazione di Visual Studio scrive il valore del Registro di sistema di **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** come **C:\VS2008\Common7\IDE\devenv.exe**, un percorso completo del file eseguibile deve essere eseguito il programma di installazione.  
  
 **Nota** perché la colonna di tipo RegLocator è 2, non è necessario specificare informazioni aggiuntive sulla versione nella tabella di firma.  
  
## <a name="running-devenvexe"></a>Esegue devenv.exe  
 Dopo aver AppSearch azione standard viene eseguito il programma di installazione, ogni proprietà nella tabella AppSearch ha un valore che punta al file devenv.exe per la versione corrispondente di Visual Studio. Se uno dei valori del Registro di sistema non sono presente, perché non è installata la versione di Visual Studio, la proprietà specificata è impostata su null.  
  
 Windows Installer supporta l'esecuzione di un eseguibile a cui fa riferimento una proprietà tramite un'azione personalizzata digita 50. L'azione personalizzata deve includere le opzioni di esecuzione di script, msidbCustomActionTypeInScript (1024) e msidbCustomActionTypeCommit (512), per garantire che il pacchetto VSPackage è stato installato prima di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere la tabella CustomAction e opzioni di esecuzione In Script azione personalizzata.  
  
 Azioni personalizzate del tipo 50 specificano la proprietà contenente il file eseguibile come valore della colonna di origine e gli argomenti della riga di comando nella colonna di destinazione.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction righe della tabella per l'esecuzione di devenv.exe  
  
|Operazione|Tipo|Origine|destinazione|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Azioni personalizzate devono essere create nella tabella InstallExecuteSequence a pianificarli per l'esecuzione durante l'installazione. Utilizzare la proprietà corrispondente in ogni riga della colonna di condizione per evitare che l'azione personalizzata viene eseguita se la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è installato nel sistema.  
  
> [!NOTE]
>  `Null` restituiscono proprietà `False` utilizzato nelle condizioni.  
  
 Il valore della colonna di sequenza per ogni azione personalizzata dipende da altri valori di sequenza nel pacchetto di Windows Installer. I valori di sequenza, verificare che le azioni personalizzate devenv.exe runas vicino possibile alla immediatamente prima dell'azione InstallFinalize standard.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Nella tabella per pianificare le azioni personalizzate devenv.exe InstallExecuteSequence  
  
|Operazione|Condizione|Sequence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)