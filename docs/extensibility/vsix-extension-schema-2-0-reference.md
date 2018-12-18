---
title: Riferimento di Schema 2.0 estensione VSIX | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7459b4292220e6bb1e5a00b912efe7eb99cce825
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-extension-schema-20-reference"></a>Riferimento di Schema 2.0 estensione VSIX
Un file manifesto di distribuzione VSIX descrive il contenuto di un pacchetto VSIX. Il formato di file non sia disciplinato da uno schema. La versione 2.0 di questo schema supporta l'aggiunta di attributi e tipi personalizzati.  Lo schema del manifesto è estensibile. Il caricatore di manifesto ignora gli elementi XML e gli attributi che non riconosce.  
  
> [!IMPORTANT]
>  Visual Studio 2015 è possibile caricare il file VSIX in formati di Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Schema del manifesto di pacchetto  
 L'elemento radice del file manifesto XML è `<PackageManifest>`, con un singolo attributo `Version`, che è la versione del formato del manifesto. Se il formato vengono apportate modifiche essenziali, verrà modificato il formato della versione. In questo argomento viene formato manifesto versione 2.0, che viene specificato nel manifesto impostando il `Version` attributo sul valore di versione = "2.0".  
  
### <a name="packagemanifest-element"></a>Elemento PackageManifest  
 All'interno di `<PackageManifest>` elemento radice, è possibile utilizzare i seguenti elementi:  
  
-   `<Metadata>` -I metadati e informazioni di annunci per il pacchetto stesso. Un solo `Metadata` l'elemento è consentito nel manifesto.  
  
-   `<Installation>` -Questa sezione definisce il modo in cui in che questo pacchetto di estensione può essere installato, inclusi gli SKU di applicazione che possa essere installato. Una sola `Installation` l'elemento è consentito nel manifesto. Un manifesto deve avere un `Installation` elemento o il pacchetto non verrà installato in qualsiasi SKU.  
  
-   `<Dependencies>` -Un elenco facoltativo delle dipendenze del pacchetto sono definiti di seguito.  
  
-   `<Assets>` -Questa sezione contiene tutti gli asset di contenuti all'interno di questo pacchetto. Senza questa sezione di questo pacchetto non superficie qualsiasi contenuto.  
  
-   `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile da consentire tutti gli altri elementi. Tutti gli elementi figlio non riconosciuti dal caricatore del manifesto vengono esposte nell'API di Gestione estensioni come gli altri oggetti XmlElement. Utilizzando tali elementi figlio, le estensioni VSIX definire dati aggiuntivi nel file manifesto del codice in esecuzione in Visual Studio è possibile accedere in fase di esecuzione. Vedere <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> e <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Elemento dei metadati  
 In questa sezione è i metadati sul pacchetto, l'identità e pubblicità informazioni. `<Metadata>` contiene gli elementi seguenti:  
  
-   `<Identity>` -Questo definisce le informazioni di identificazione del pacchetto e include gli attributi seguenti:  
  
    -   `Id` -Questo attributo deve essere un ID univoco per il pacchetto scelto dall'autore. Il nome deve essere specificato esattamente come tipi CLR sono spazi dei nomi: Company.Product.Feature.Name. Il `Id` attributo è limitata a 100 caratteri.  
  
    -   `Version` -Definisce la versione di questo pacchetto e il relativo contenuto. Questo attributo viene indicato il formato di controllo delle versioni di assembly CLR: Major (1.2.40308.00). Un pacchetto con un numero di versione superiore viene considerato aggiornamenti del pacchetto e può essere installato tramite le versioni esistenti.  
  
    -   `Language` -Questo attributo è la lingua predefinita per il pacchetto e corrisponde ai dati testuali di questo manifesto. Questo attributo segue la convenzione di codice delle impostazioni locali CLR per gli assembly di risorse, ad esempio: en-us, en, fr-fr. È possibile specificare `neutral` per dichiarare un'estensione di lingua che verrà eseguito in qualsiasi versione di Visual Studio. Il valore predefinito è `neutral`.  
  
    -   `Publisher` -Questo attributo identifica il server di pubblicazione del pacchetto, società o un singolo nome. Il `Publisher` attributo è limitata a 100 caratteri.  
  
-   `<DisplayName>` -Questo elemento specifica il nome del pacchetto intuitiva che viene visualizzato nell'UI Gestione estensioni. Il `DisplayName` contenuto è limitato a 50 caratteri.  
  
-   `<Description>` -Questo elemento facoltativo è una breve descrizione del pacchetto e il relativo contenuto viene visualizzata in Gestione estensioni UI. Il `Description` contenuto può contenere qualsiasi testo che si desidera, ma è limitato a 1000 caratteri.  
  
-   `<MoreInfo>` -Questo elemento facoltativo è un URL di una pagina online che contiene una descrizione completa di questo pacchetto. Il protocollo deve essere specificato come http.  
  
-   `<License>` -Questo elemento facoltativo è un percorso relativo in un file di licenza (con estensione txt,. RTF) contenuto nel pacchetto.  
  
-   `<ReleaseNotes>` -Questo elemento facoltativo è un percorso relativo in un file di note sulla versione contenuto nel pacchetto (con estensione txt,. RTF) oppure un URL a un sito Web che consente di visualizzare le note sulla versione.  
  
-   `<Icon>` -Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg, ico) contenuto nel pacchetto. L'immagine dell'icona devono essere 32 x 32 pixel (o verrà ridotta a tale dimensione) e viene visualizzato nell'interfaccia utente di listview. Se non `Icon` elemento viene specificato, l'interfaccia utente utilizza un valore predefinito.  
  
-   `<PreviewImage>` -Questo elemento facoltativo è un percorso relativo a un file di immagine (png, bmp, jpeg) contenuto nel pacchetto. L'immagine di anteprima deve essere di 200 x 200 pixel e visualizzato nei dettagli dell'interfaccia utente. Se non `PreviewImage` elemento viene specificato, l'interfaccia utente utilizza un valore predefinito.  
  
-   `<Tags>` -Questo elemento facoltativo sono elencati i tag di testo delimitato da punto e virgola aggiuntivo che vengono utilizzati per suggerimenti per la ricerca. Il `Tags` elemento è limitato a 100 caratteri.  
  
-   `<GettingStartedGuide>` -Questo elemento facoltativo è un percorso relativo in un file HTML o un URL a un sito Web che contiene informazioni su come usare l'estensione o il contenuto all'interno di questo pacchetto. Questa guida viene avviata come parte di un'installazione.  
  
-   `<AnyElement>*` -Lo schema del manifesto è sufficientemente flessibile da consentire tutti gli altri elementi. Tutti gli elementi figlio che non sono riconosciuti dal caricatore del manifesto vengono esposti come un elenco di oggetti XmlElement. Utilizza tali elementi figlio, le estensioni VSIX possono definiscono dati aggiuntivi nel file manifesto e li si enumerano in fase di esecuzione.  
  
### <a name="installation-element"></a>Elemento di installazione  
 In questa sezione definisce il modo in cui che è possibile installare questo pacchetto e gli SKU di applicazione che possa essere installato in. In questa sezione contiene gli attributi seguenti:  
  
-   `Experimental` -Impostare questo attributo su true se si dispone di un'estensione che è attualmente installata per tutti gli utenti, ma si sviluppa una versione aggiornata nello stesso computer. Ad esempio, se sono stati installati MyExtension 1.0 per tutti gli utenti, ma si desidera eseguire il debug MyExtension 2.0 nello stesso computer, impostare sperimentale = "true". Questo attributo è disponibile in Visual Studio 2015 Update 1 e versioni successive.  
  
-   `Scope` -Questo attributo può accettare il valore "Globale" o "ProductExtension":  
  
    -   "Globali" Specifica che l'installazione non è definito per uno specifico SKU. Ad esempio, questo valore viene utilizzato quando viene installato un SDK di estensione.  
  
    -   "ProductExtension" specifica un'estensione VSIX tradizionale (versione 1.0) con ambito a singoli SKU di Visual Studio è installata. Rappresenta il valore predefinito.  
  
-   `AllUsers` -Questo attributo facoltativo specifica se il pacchetto verrà installato per tutti gli utenti. Per impostazione predefinita, questo attributo è false, che indica che il pacchetto per ogni utente. (Quando si imposta questo valore su true, l'utente di installazione necessario innalzare di livello a livello di privilegi di amministratore per installare il progetto VSIX risultante.  
  
-   `InstalledByMsi` -Questo attributo facoltativo specifica se il pacchetto viene installato da un file MSI. Pacchetti installati da un file MSI vengono installati e gestiti dal file MSI (programmi e funzionalità) e non da Visual Studio Gestione estensioni.  Per impostazione predefinita, questo attributo è false, che consente di specificare che il pacchetto non è installato da un file MSI.  
  
-   `SystemComponent` -Questo attributo facoltativo specifica se il pacchetto deve essere considerato un componente del sistema. I componenti di sistema non mostrano nell'UI Extension Manager e non possono essere aggiornati. Per impostazione predefinita, questo attributo è false, che consente di specificare che il pacchetto non è un componente del sistema.  
  
-   `AnyAttribute*` -La `Installation` elemento accetta un set aperto di attributi che saranno esposti in fase di esecuzione come un dizionario di coppia nome-valore.  
  
-   `<InstallationTarget>` : Questo elemento controlla il percorso in cui il programma di installazione VSIX installa il pacchetto. Se il valore di `Scope` attributo è "ProductExtension" il pacchetto di destinazione deve essere uno SKU di cui è installato un file manifesto come parte del relativo contenuto per annunciare la disponibilità di estensioni. Il `<InstallationTarget>` elemento offre i seguenti attributi quando il `Scope` presenta esplicita o il valore predefinito "ProductExtension":  
  
    -   `Id` -Questo attributo identifica il pacchetto.  L'attributo segue la convenzione di spazio dei nomi: Company.Product.Feature.Name. Il `Id` attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri. Valori previsti:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` -Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate dello SKU. Un pacchetto può descrivere in dettaglio le versioni di SKU che supporta. La notazione di intervallo di versione è [10.0 11.0], dove  
  
        -   [-versione minima inclusiva.  
  
        -   ]-versione massima inclusiva.  
  
        -   (-versione minima esclusiva.  
  
        -   )-versione massima esclusiva.  
  
        -   Versione unica # - solo la versione specificata.  
  
        > [!IMPORTANT]
        >  Versione 2.0 dello Schema VSIX è stato introdotto in Visual Studio 2012. Per utilizzare lo schema si deve disporre di Visual Studio 2012 o versioni successive installato nel computer e utilizza VSIXInstaller.exe che fa parte di tale prodotto. È possibile usare le versioni precedenti di Visual Studio con un Visual Studio 2012 o versioni successive VSIXInstaller, ma solo utilizzando le versioni più recenti del programma di installazione.  
  
    -   `AnyAttribute*` -La `<InstallationTarget>` elemento consente a un set aperto di attributi che verranno esposte in fase di esecuzione come un dizionario di coppia nome-valore.  
  
### <a name="dependencies-element"></a>Elemento Dependencies  
 Questo elemento contiene un elenco di dipendenze che dichiara questo pacchetto. Se vengono specificate tutte le dipendenze, tali pacchetti (identificato da loro `Id`) deve essere installato prima di.  
  
-   `<Dependency>` elemento - l'elemento figlio ha gli attributi seguenti:  
  
    -   `Id` -Questo attributo deve essere un ID univoco per il pacchetto dipendente. Questo valore di identità deve corrispondere il `<Metadata><Identity>Id` attributo di un pacchetto di cui dipende questo pacchetto. Il `Id` attributo segue la convenzione di spazio dei nomi: Company.Product.Feature.Name. L'attributo può contenere solo caratteri alfanumerici ed è limitato a 100 caratteri.  
  
    -   `Version` -Questo attributo specifica un intervallo di versioni con le versioni minime e massime supportate dello SKU. Un pacchetto può descrivere in dettaglio le versioni di SKU che supporta. La notazione di intervallo di versione è [12.0, 13.0], dove:  
  
        -   [-versione minima inclusiva.  
  
        -   ]-versione massima inclusiva.  
  
        -   (-versione minima esclusiva.  
  
        -   )-versione massima esclusiva.  
  
        -   Versione unica # - solo la versione specificata.  
  
    -   `DisplayName` -L'attributo è il nome visualizzato del pacchetto dipendente che viene utilizzato per gli elementi dell'interfaccia utente, ad esempio le finestre di dialogo e i messaggi di errore. L'attributo è facoltativo, a meno che non è installato il pacchetto dipendente dal file MSI.  
  
    -   `Location` -Questo attributo facoltativo specifica il percorso relativo all'interno di questa estensione VSIX a un pacchetto VSIX annidato o un URL nel percorso di download per la dipendenza. Questo attributo viene utilizzato per consentire all'utente di individuare il pacchetto dei prerequisiti.  
  
    -   `AnyAttribute*` -La `Dependency` elemento accetta un set aperto di attributi che saranno esposti in fase di esecuzione come un dizionario di coppia nome-valore.  
  
### <a name="assets-element"></a>Elemento Asset  
 Questo elemento contiene un elenco di `<Asset>` tag per ogni elemento di estensione o il contenuto è esposto dal pacchetto.  
  
-   `<Asset>` : Questo elemento contiene elementi e gli attributi seguenti:  
  
    -   `Type` -Questo è il tipo di estensione o contenuto rappresentato da questo elemento. Ogni `<Asset>` l'elemento deve avere un unico `Type`, ma più `<Asset>` elementi possono avere lo stesso `Type`. Questo attributo deve essere rappresentato come un nome completo, in base alle convenzioni di spazio dei nomi. I tipi noti sono:  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         È possibile creare tipi personalizzati e assegnare loro nomi univoci. In fase di esecuzione all'interno di Visual Studio, il codice di enumerare e accedere a questi tipi personalizzati tramite l'API di Gestione estensioni.  
  
    -   Percorso: il percorso relativo al file o cartella all'interno del pacchetto che contiene la risorsa.  
  
    -   `AnyAttribute*` -Un set aperto di attributi che verranno esposte in fase di esecuzione come un dizionario di coppia nome-valore.  
  
         `<AnyElement>*` -Qualsiasi contenuto strutturato è consentita tra un `<Asset>` iniziano e tag di fine. Tutti gli elementi vengono esposti come un elenco di oggetti XmlElement. Le estensioni VSIX possono definire i metadati specifici del tipo strutturato nel file manifesto e li si enumerano in fase di esecuzione.  
  
### <a name="sample-manifest"></a>Manifesto di esempio  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)