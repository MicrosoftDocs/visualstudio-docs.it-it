---
title: Gallerie private | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5226ff7a4ed77333d2a6f9287f129c6a6d754cac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="private-galleries"></a>Private Galleries
È possibile condividere i controlli, modelli e strumenti che si sviluppano inserendoli in un *raccolta privata* sulla rete intranet per l'organizzazione, come indicato di seguito:  
  
-   Creare un Atom feed RSS in una posizione centrale configurata opportunamente (repository) nella rete intranet. Per ulteriori informazioni, vedere [procedura: creare un Feed Atom per una raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuire un file. pkgdef che descrive la raccolta privata. Si consiglia questa configurazione per gli amministratori che desiderano connettersi a una raccolta privata a più computer contemporaneamente.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiunta di una raccolta privata a estensioni e aggiornamenti in Visual Studio  
 Quando una raccolta privata è disponibile, è possibile aggiungere a **estensioni e aggiornamenti** in Visual Studio.  
  
 ![Finestra di dialogo Aggiungi gestore estensioni](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a estensioni e aggiornamenti  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Nel **ambiente** nodo, seleziona **estensioni e aggiornamenti**.  
  
3.  Scegliere il pulsante **Aggiungi**.  
  
4.  Nel **nome** immettere un nome per la raccolta privata, ad esempio, `My Gallery`.  
  
5.  Nel **URL** immettere l'URL del feed Atom o sito di SharePoint che ospita la raccolta privata.  
  
    1.  Se l'host è un feed Atom che si connette a una raccolta privata, l'URL sarà simile a questo: http://www.mywebsite/mygallery/atom.xml.  Questo URL può fare riferimento a un file o un percorso di rete.  
  
    2.  Se l'host è un sito di SharePoint, l'URL sarà simile a questo: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>La gestione di raccolte Private  
 Un amministratore può renderla una raccolta privata disponibile per più computer allo stesso tempo modificando il Registro di sistema in ogni computer. A tale scopo, creare un file. pkgdef che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è come indicato di seguito.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Per ulteriori informazioni, vedere [procedura: gestire una privata raccolta da utilizzo del Registro di sistema le impostazioni](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>L'installazione delle estensioni da una raccolta privata  
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **estensioni e aggiornamenti**. La procedura seguente utilizza una raccolta privata denominata `My Gallery`.  
  
 ![L'installazione della Galleria privata di gestione di estensione](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare le estensioni da una raccolta privata  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, selezionare **estensioni Online**, quindi selezionare **raccolta personale**.  
  
3.  Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **scaricare** pulsante.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>L'aggiornamento delle estensioni da una raccolta privata  
 Come le nuove versioni delle estensioni di Visual Studio vengono registrate nella raccolta privata, è possibile aggiornare le estensioni che è stato installato. La procedura seguente utilizza una raccolta privata denominata `My Repository`.  
  
 ![Aggiornamento della Galleria privata di Gestione estensioni](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privata  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, selezionare **aggiornamenti**, quindi selezionare **Repository My**.  
  
3.  Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **aggiornamento** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)