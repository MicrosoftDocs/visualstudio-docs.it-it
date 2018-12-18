---
title: Specifica i gestori di File per estensioni di File | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d0086f8badb32431c85f16e1f74fe8f186c9b2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Specifica i gestori di File per estensioni di File
Esistono diversi modi per determinare l'applicazione che gestisce un file che contiene un'estensione di file specifico. I verbi OpenWithList e OpenWithProgids sono due modi per specificare i gestori di file nella voce del Registro di sistema per l'estensione di file.  
  
## <a name="openwithlist-verb"></a>Verbo OpenWithList  
 Quando si fa clic su un file in Esplora risorse, vedere il **aprire** comando. Se più di un prodotto è associato a un'estensione, viene visualizzato un **Apri con** sottomenu.  
  
 È possibile registrare applicazioni diverse per aprire un'estensione impostando la chiave OpenWithList per l'estensione di file in HKEY_CLASSES_ROOT. Le applicazioni elencate in questa chiave per un'estensione di file vengono visualizzati sotto il **applicazioni consigliate** intestazione nel **Apri con** la finestra di dialogo. L'esempio seguente mostra le applicazioni registrate per aprire l'estensione di file VCPROJ.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Le chiavi che specifica le applicazioni sono nell'elenco in HKEY_CLASSES_ROOT\Applications.  
  
 Aggiunta di una chiave OpenWithList, si dichiara che l'applicazione supporta un'estensione di file, anche se un'altra applicazione assume la proprietà dell'estensione. Potrebbe trattarsi di una versione futura dell'applicazione o un'altra applicazione.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificatore programmatico (ProgID) sono versioni descrittive ClassID che identificano una versione di un'applicazione o un oggetto COM. Ogni oggetto condiviso che può essere creato deve avere il proprio ProgID. Ad esempio, VisualStudio.DTE.7.1 avvia Visual Studio .NET 2003 durante l'avvio di VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Come proprietario di un tipo di progetto o un tipo di elemento di progetto, è necessario creare un ProgID specifico della versione per l'estensione di file. Questi ProgID possono essere ridondanti in più di un ProgID può avviare l'applicazione stessa. Per ulteriori informazioni, vedere [registrazione verbi per estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Per evitare la duplicazione con la registrazione di altri fornitori, utilizzare la seguente convenzione di denominazione per il file con controllo delle versioni ProgID:  
  
|Estensione di file|Controllo delle versioni di ProgID|  
|--------------------|----------------------|  
|. Extension|ProductName. extension.versionMajor.versionMinor|  
  
 È possibile registrare diverse applicazioni che sono in grado di aprire una particolare estensione di file mediante l'aggiunta di ProgID con controllo delle versioni come valori per il HKEY_CLASSES_ROOT\\*\<estensione >*\OpenWithProgids chiave. Questa chiave del Registro di sistema contiene un elenco di ProgID alternativo associato all'estensione di file. Le applicazioni associate ai ProgID elencati vengono visualizzati nel **Apri con * * * il nome del prodotto* sottomenu. Se viene specificata l'applicazione stessa in entrambe le `OpenWithList` e `OpenWithProgids` chiavi, il sistema operativo unisce i duplicati.  
  
> [!NOTE]
>  Il `OpenWithProgids` chiavi è supportata solo in Windows XP. Poiché altri sistemi operativi ignorare questa chiave, non utilizzarlo come la registrazione sola per i gestori di file. Usare questa chiave per fornire una migliore esperienza utente in Windows XP.  
  
 Aggiungere i ProgID desiderati come valori di tipo REG_NONE. Il codice seguente viene fornito un esempio di registrazione di ProgID per un'estensione di file (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Il valore ProgID specificato, come il valore predefinito per l'estensione del file è il gestore di file predefinito. Se si modifica il ProgID per un'estensione di file forniti con una versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o che può essere preso in carico da altre applicazioni, quindi è necessario registrare il `OpenWithProgids` chiave per l'estensione di file e specificare il nuovo ProgID nell'elenco insieme a gli ID di programma precedente che è supportata. Ad esempio:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Se il vecchio ProgID ha verbi associati, in questi verbi verranno visualizzati anche in **Apri con** *Product Name* nel menu di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [Sulle estensioni di File](../extensibility/about-file-name-extensions.md)   
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)