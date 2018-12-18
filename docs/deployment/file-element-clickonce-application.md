---
title: '&lt;file&gt; elemento (applicazione ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: "24"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 9e3e6429f32c8939960816e576f9aabefd4763e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file&gt; elemento (applicazione ClickOnce)
Identifica tutti i file scaricati e utilizzati dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `file` è facoltativo. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome del file.|  
|`size`|Obbligatorio. Specifica le dimensioni, in byte, del file.|  
|`group`|Facoltativo, se il `optional` attributo viene omesso o impostato su `false`; obbligatorio se `optional` è `true`. Il nome del gruppo a cui appartiene questo file. Il nome può essere qualsiasi valore stringa Unicode scelto dallo sviluppatore e viene utilizzato per il download dei file su richiesta con la <xref:System.Deployment.Application.ApplicationDeployment> classe.|  
|`optional`|Facoltativo. Specifica se il file deve essere download quando l'applicazione viene innanzitutto eseguito, o se il file deve trovarsi solo nel server fino a quando non viene richiesto dall'applicazione su richiesta. Se `false` o non definito, il file viene scaricato quando l'applicazione o della prima esecuzione installato. Se `true`, `group` deve essere specificato per il manifesto dell'applicazione sia valido. `optional`non può essere true se `writeableType` è specificato con il valore `applicationData`.|  
|`writeableType`|Facoltativo. Specifica che il file sia un file di dati. Attualmente l'unico valore valido è `applicationData`.|  
  
## <a name="typelib"></a>libreria dei tipi  
 Il `typelib` elemento è un elemento figlio facoltativo dell'elemento file. L'elemento descrive una libreria dei tipi a cui appartiene il componente COM. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`tlbid`|Obbligatorio. GUID assegnato alla libreria dei tipi.|  
|`version`|Obbligatorio. Il numero di versione della libreria dei tipi.|  
|`helpdir`|Obbligatorio. La directory che contiene i file della Guida per il componente. Può essere di lunghezza zero.|  
|`resourceid`|Facoltativo. Rappresentazione di stringa esadecimale dell'identificatore delle impostazioni locali (LCID). È uno a quattro cifre esadecimali senza il prefisso 0x e senza zeri iniziali. L'identificatore LCID può avere un identificatore di varietà di lingua neutra.|  
|`flags`|Facoltativo. Rappresentazione di stringa dei flag di libreria di tipo per questa libreria dei tipi. In particolare, deve essere uno dei "RESTRICTED", "Controllo", "HIDDEN" e "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 Il `comClass` elemento è un elemento figlio facoltativo del `file` elemento, ma è obbligatorio se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che si desidera distribuire mediante componenti COM senza registrazione L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`clsid`|Obbligatorio. L'ID di classe del componente COM espresso come GUID.|  
|`description`|Facoltativo. Nome della classe.|  
|`threadingModel`|Facoltativo. Il modello di threading utilizzato dalle classi COM nel processo. Se questa proprietà è null, non viene utilizzato alcun modello di threading. Il componente viene creato nel thread principale del client e vengono effettuato il marshalling di chiamate da altri thread a questo thread. Nell'elenco seguente illustra i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|  
|`tlbid`|Facoltativo. GUID della libreria dei tipi per questo componente COM.|  
|`progid`|Facoltativo. Identificatore a livello di codice dipendente dalla versione associato al componente COM. Il formato di un `ProgID` è `<vendor>.<component>.<version>`.|  
|`miscStatus`|Facoltativo. I duplicati nell'assembly manifesto le informazioni fornite dal `MiscStatus` chiave del Registro di sistema. Se i valori per il `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, o `miscStatusThumbnail` attributi non vengono trovati, il valore predefinito corrispondente elencato `miscStatus` viene utilizzato per gli attributi mancanti. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusIcon`|Facoltativo. I duplicati nell'assembly manifesto le informazioni fornite da DVASPECT_ICON. E può fornire un'icona di un oggetto. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `Miscstatus` valori di chiave del Registro di sistema.|  
|`miscStatusContent`|Facoltativo. I duplicati nell'assembly manifesto le informazioni fornite da DVASPECT_CONTENT. È possibile fornire un documento composito visualizzabile per una schermata o una stampante. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusDocPrint`|Facoltativo. I duplicati nell'assembly manifesto le informazioni fornite da DVASPECT_DOCPRINT. E può fornire una rappresentazione dell'oggetto visualizzabile sullo schermo come se fosse a una stampante. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusThumbnail`|Facoltativo. I duplicati in un assembly manifesto le informazioni fornite da DVASPECT_THUMBNAIL. E può fornire un'anteprima di un oggetto visualizzabile in uno strumento di esplorazione. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Il `comInterfaceExternalProxyStub` elemento è un elemento figlio facoltativo del `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che si desidera distribuire mediante componenti COM senza registrazione L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`iid`|Obbligatorio. L'ID (IID) viene servita dal proxy di interfaccia. L'IID deve avere tra parentesi quadre.|  
|`baseInterface`|Facoltativo. L'IID dell'interfaccia da cui l'interfaccia a cui fa riferimento `iid` derivato.|  
|`numMethods`|Facoltativo. Il numero di metodi implementati dall'interfaccia.|  
|`name`|Facoltativo. Il nome dell'interfaccia che verrà visualizzato nel codice.|  
|`tlbid`|Facoltativo. La libreria dei tipi contenente la descrizione dell'interfaccia specificata per il `iid` attributo.|  
|`proxyStubClass32`|Facoltativo. Esegue il mapping di un IID a un CLSID nelle DLL proxy a 32 bit.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Il `comInterfaceProxyStub` elemento è un elemento figlio facoltativo del `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che si desidera distribuire mediante componenti COM senza registrazione L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`iid`|Obbligatorio. L'ID (IID) viene servita dal proxy di interfaccia. L'IID deve avere tra parentesi quadre.|  
|`baseInterface`|Facoltativo. L'IID dell'interfaccia da cui l'interfaccia a cui fa riferimento `iid` derivato.|  
|`numMethods`|Facoltativo. Il numero di metodi implementati dall'interfaccia.|  
|`Name`|Facoltativo. Il nome dell'interfaccia che verrà visualizzato nel codice.|  
|`Tlbid`|Facoltativo. La libreria dei tipi contenente la descrizione dell'interfaccia specificata per il `iid` attributo.|  
|`proxyStubClass32`|Facoltativo. Esegue il mapping di un IID a un CLSID nelle DLL proxy a 32 bit.|  
|`threadingModel`|Facoltativo. Facoltativo. Il modello di threading utilizzato dalle classi COM nel processo. Se questa proprietà è null, non viene utilizzato alcun modello di threading. Il componente viene creato nel thread principale del client e vengono effettuato il marshalling di chiamate da altri thread a questo thread. Nell'elenco seguente illustra i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 Il `windowClass` elemento è un elemento figlio facoltativo del `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che si desidera distribuire mediante componenti COM senza registrazione L'elemento fa riferimento a una classe di finestra definita dal componente COM che deve avere un versione applicato. L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`versioned`|Facoltativo. Controlla se la finestra interna classe nome usato nella registrazione contiene la versione dell'assembly che contiene la classe di finestra. Il valore di questo attributo può essere `yes` o `no`. Il valore predefinito è `yes`. Il valore `no` deve essere utilizzato solo se la stessa classe di finestra è definita da un componente side-by-side e un componente non-side-by-side equivalente e si desidera vengano considerati come la stessa classe della finestra. Si noti che si applicano le normali regole di registrazione della classe di finestra, solo il primo componente che registra la classe della finestra sarà in grado di registrare, perché non dispone di una versione applicata.|  
  
## <a name="hash"></a>hash  
 Il `hash` elemento è un elemento figlio facoltativo del `file` elemento. Il `hash` elemento non ha attributi.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]utilizza un hash algoritmico di tutti i file in un'applicazione come un controllo di sicurezza, per verificare che nessuno dei file sono stati modificati dopo la distribuzione. Se il `hash` elemento non viene incluso, questo controllo non verrà eseguito. Pertanto, omettendo il `hash` elemento non è consigliato.  
  
 Se un manifesto contiene un file che non è stato eseguito l'hashing, il manifesto non può essere digitale firmato, perché gli utenti non è possibile verificare il contenuto di un file senza hash.  
  
## <a name="dsigtransforms"></a>dsig: Transforms  
 Il `dsig:Transforms` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:Transforms` elemento non ha attributi.  
  
## <a name="dsigtransform"></a>dsig: Transform  
 Il `dsig:Transform` elemento è un elemento figlio obbligatorio del `dsig:Transforms` elemento. Il `dsig:Transform` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 Il `dsig:DigestMethod` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:DigestMethod` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per calcolare il digest per questo file. L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig:  
 Il `dsig:DigestValue` elemento è un elemento figlio obbligatorio del `hash` elemento. Il `dsig:DigestValue` elemento non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.  
  
## <a name="remarks"></a>Note  
 Questo elemento identifica tutti i file membri che costituiscono l'applicazione e, in particolare, i valori hash per la verifica dei file. Questo elemento può anche includere dati sull'isolamento modello COM (Component Object) associati al file. Se viene modificato un file, file manifesto dell'applicazione deve inoltre essere aggiornato per riflettere la modifica.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra `file` elementi in un'applicazione del manifesto per un'applicazione distribuita mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)