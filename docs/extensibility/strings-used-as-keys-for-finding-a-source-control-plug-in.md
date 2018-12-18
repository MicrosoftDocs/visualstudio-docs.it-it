---
title: Stringhe usate come chiavi per la ricerca di plug-in un controllo del codice sorgente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a42eebe67ce1f611cf6e48883bc09139f241e658
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Stringhe usate come chiavi per la ricerca di un controllo del codice sorgente plug-in
Le stringhe seguenti sono le chiavi per l'accesso alle informazioni di controllo del codice sorgente plug-nel Registro di sistema.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, e `STR_SCCPROVIDERNAME` sono le chiavi del Registro di sistema o i valori utilizzati per registrare una DLL come un plug-in del controllo del codice sorgente per Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, e `SCC_STATUS_FILE` vengono utilizzati per descrivere il formato del MSSCCPRJ. File SCC.  
  
## <a name="string-keys-and-values"></a>Chiavi String e valori  
  
|Chiave|Valore|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Controllo del codice sorgente|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. CONTROLLO CONFIGURAZIONE SISTEMA|  
|`SCC_KEY`|CONTROLLO CONFIGURAZIONE SISTEMA|  
|`SCC_FILE_SIGNATURE`|Un file di controllo del codice sorgente|  
|`SCC_NSE`|Estensione Namespace|  
|`SCC_NSE_PREFIX`|Prefisso Protocal|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Procedura: installare un plug-in controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)