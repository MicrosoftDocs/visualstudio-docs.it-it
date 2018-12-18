---
title: '&lt;InstallChecks&gt; elemento (programma di avvio automatico) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcfd8aaa0048cac3fb9a33c7974132655de87a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; elemento (programma di avvio automatico)
Il `InstallChecks` elemento consente di avviare una serie di test sul computer locale per assicurarsi che siano stati installati tutti i prerequisiti appropriati di un'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `AssemblyCheck`, il programma di avvio verrà verificare che l'assembly identificato dall'elemento presente nella global assembly cache (GAC). Non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obbligatorio. Il nome completo dell'assembly da controllare.|  
|`PublicKeyToken`|Obbligatorio. Forma abbreviata della chiave pubblica associato a questo assembly un nome sicuro. Tutti gli assembly memorizzati nella GAC devono avere un nome, una versione e una chiave pubblica.|  
|`Version`|Obbligatorio. La versione dell'assembly.<br /><br /> Il numero di versione ha il formato \< *versione principale*>.\< *versione secondaria*>.\< *versione build*>.\< *revisione*>.|  
|`Language`|Facoltativo. La lingua di un assembly localizzato. Il valore predefinito è `neutral`.|  
|`ProcessorArchitecture`|Facoltativo. Il processore del computer di destinazione dell'installazione. Il valore predefinito è `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `ExternalCheck`, il programma di avvio automatico eseguire il programma esterno denominato in un processo separato e archivia il codice di uscita nella proprietà indicata da `Property`. `ExternalCheck` è utile per l'implementazione di controlli di dipendenze complesse, oppure quando viene creata un'istanza di l'unico modo per verificare l'esistenza di un componente.  
  
 `ExternalCheck` non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obbligatorio. Il programma esterno da eseguire. Il programma deve far parte del pacchetto di distribuzione di installazione.|  
|`Arguments`|Facoltativo. Fornisce gli argomenti della riga di comando per il file eseguibile denominato da `PackageFile`.|  
  
## <a name="filecheck"></a>FileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `FileCheck`, il programma di avvio determina se il file denominato esiste e restituire il numero di versione del file. Se il file non dispone di un numero di versione, il programma di avvio automatico imposta la proprietà denominata da `Property` su 0. Se il file non esiste, `Property` non è impostata su qualsiasi valore.  
  
 `FileCheck` non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obbligatorio. Il nome del file da trovare.|  
|`SearchPath`|Obbligatorio. Il disco o una cartella in cui cercare il file. Deve trattarsi di un percorso relativo, se `SpecialFolder` viene assegnato; in caso contrario, deve essere un percorso assoluto.|  
|`SpecialFolder`|Facoltativo. Una cartella con un significato speciale per Windows o per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il valore predefinito è interpretare `SearchPath` come un percorso assoluto. Di seguito vengono elencati i valori validi:<br /><br /> `AppDataFolder`. La cartella application data per questo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione; specifici dell'utente corrente.<br /><br /> `CommonAppDataFolder`. La cartella application data utilizzata da tutti gli utenti.<br /><br /> `CommonFilesFolder`. La cartella di file comuni per l'utente corrente.<br /><br /> `LocalDataAppFolder`. La cartella di dati per le applicazioni non comuni.<br /><br /> `ProgramFilesFolder`. La cartella di file di programma standard per applicazioni a 32 bit.<br /><br /> `StartUpFolder`. La cartella che contiene tutte le applicazioni eseguite all'avvio del sistema.<br /><br /> `SystemFolder`. La cartella che contiene le DLL di sistema a 32 bit.<br /><br /> `WindowsFolder`. La cartella che contiene l'installazione del sistema Windows.<br /><br /> `WindowsVolume`. L'unità o partizione che contiene l'installazione del sistema Windows.|  
|`SearchDepth`|Facoltativo. La profondità in corrispondenza del quale eseguire la ricerca delle sottocartelle per il file denominato. La ricerca viene eseguita in profondità. Il valore predefinito è 0, che limita la ricerca nella cartella di livello superiore specificato da `SpecialFolder` e **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `MsiProductCheck`, il programma di avvio controlla se l'installazione di Microsoft Windows Installer specificato è stato eseguito fino al completamento. Il valore della proprietà è impostato in base allo stato del prodotto installato. Un valore positivo indica che il prodotto sia installato, 0 o -1 indica non è installato. (Vedere la funzione di Windows Installer SDK MsiQueryFeatureState per altre informazioni). . Se Windows Installer non è installato nel computer, `Property` non è impostata.  
  
 `MsiProductCheck` non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obbligatorio. Il GUID per il prodotto installato.|  
|`Feature`|Facoltativo. GUID per una funzionalità specifica dell'applicazione installata.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `RegistryCheck`, il programma di avvio automatico verifica se la chiave del Registro di sistema presente o se è impostata sul valore indicato.  
  
 `RegistryCheck` non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema.|  
|`Value`|Facoltativo. Il nome del valore del Registro di sistema da recuperare. Il valore predefinito è per ottenere il testo del valore predefinito. `Value` deve essere una stringa o un valore DWORD.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`. Per ogni istanza di `RegistryFileCheck`, il programma di avvio automatico recupera la versione del file specificato, tentando innanzitutto di recuperare il percorso del file dalla chiave del Registro di sistema specificata. Ciò è particolarmente utile se si desidera cercare un file in una directory specificata come valore del Registro di sistema.  
  
 `RegistryFileCheck` non contiene elementi e presenta i seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio. Il nome della proprietà per archiviare il risultato. Questa proprietà è possibile fare riferimento da un test di sotto di `InstallConditions` elemento che è un elemento figlio del `Command` elemento. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio. Nome della chiave del Registro di sistema. Il valore viene interpretato come il percorso in un file, a meno che il `File` attributo è impostato. Se questa chiave non esiste, `Property` non è impostata.|  
|`Value`|Facoltativo. Il nome del valore del Registro di sistema da recuperare. Il valore predefinito è per ottenere il testo del valore predefinito. `Value` deve essere una stringa.|  
|`FileName`|Facoltativo. Il nome di un file. Se specificato, il valore ottenuto dalla chiave del Registro di sistema viene considerato un percorso di directory e questo nome viene aggiunto a esso. Se non specificato, il valore restituito dal Registro di sistema viene considerato il percorso completo di un file.|  
|`SearchDepth`|Facoltativo. La profondità in corrispondenza del quale eseguire la ricerca delle sottocartelle per il file denominato. La ricerca viene eseguita in profondità. Il valore predefinito è 0, che limita la ricerca nella cartella di livello superiore specificato dal valore della chiave del Registro di sistema.|  
  
## <a name="remarks"></a>Note  
 Mentre gli elementi sotto `InstallChecks` definire i test da eseguire, senza eseguirli. Per eseguire i test, è necessario creare `Command` elementi di sotto di `Commands` elemento.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra il `InstallChecks` elemento perché è usato nel file del prodotto per il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Quando `InstallChecks` vengono valutate, si ottengono le proprietà. Le proprietà vengono quindi usate da `InstallConditions` per determinare se un pacchetto debba installare, ignorare o esito negativo. La tabella seguente elenca le `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Se qualsiasi `FailIf` condizione restituisce true, il pacchetto avrà esito negativo. Il resto delle condizioni non verranno valutato.|  
|`BypassIf`|Se qualsiasi `BypassIf` condizione restituisce true, il pacchetto verrà ignorato. Il resto delle condizioni non verranno valutato.|  
  
## <a name="predefined-properties"></a>Proprietà predefinite  
 La tabella seguente elenca i `BypassIf` e `FailIf` elementi:  
  
|Proprietà|Note|Valori possibili|  
|--------------|-----------|---------------------|  
|`Version9X`|Numero di versione di un sistema operativo di Windows 9x X.|4.10 = Windows 98|  
|`VersionNT`|Numero di versione del sistema operativo basato su Windows NT.|ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Numero di versione del sistema operativo a 64 bit basato su Windows NT.|Come indicato in precedenza.|  
|`VersionMsi`|Numero di versione del servizio Windows Installer.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Specifica se un utente con privilegi di amministratore in un sistema operativo basato su Windows NT.|0 non = privilegi di amministratore<br /><br /> 1 = i privilegi di amministratore|  
  
 Ad esempio, per bloccare l'installazione in un computer che eseguono Windows 95, utilizzare codice analogo al seguente:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<I comandi > elemento](../deployment/commands-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)