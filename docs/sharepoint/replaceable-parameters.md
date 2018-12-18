---
title: Parametri sostituibili | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa002f58ffd749cef9a4cbf9b536a36d7901b105
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="replaceable-parameters"></a>Parametri sostituibili
  Parametri sostituibili, o *token*, può essere utilizzato nei file di progetto per fornire valori per gli elementi di soluzione SharePoint i cui valori effettivi non sono noti in fase di progettazione. La relativa funzione è simile a quella dei token del modello standard di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [parametri di modello](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Formato di token  
 I token iniziano e terminano con un simbolo di dollaro ($). Quando un progetto viene creato un pacchetto in un file di pacchetto (con estensione wsp) di soluzione SharePoint in fase di distribuzione, eventuali token usati vengono sostituiti con i valori effettivi. Ad esempio, il token **$SharePoint.Package.Name$** potrebbe essere risolto per la stringa "Test del pacchetto di SharePoint".  
  
## <a name="token-rules"></a>Regole dei token  
 Le regole seguenti si applicano ai token:  
  
-   Token possono essere specificati in una riga.  
  
-   Token non possono estendersi su più righe.  
  
-   Lo stesso token può essere specificato più volte sulla stessa riga e nello stesso file.  
  
-   È possibile specificare token diversi nella stessa riga.  
  
 Token che non rispettano queste regole vengono ignorati senza fornire un avviso o errore.  
  
 La sostituzione dei token con valori di stringa viene eseguita immediatamente dopo la trasformazione del manifesto, consentendo in tal modo i modelli di manifesto modificati da un utente per utilizzare i token.  
  
### <a name="token-name-resolution"></a>Risoluzione dei nomi di token  
 Nella maggior parte dei casi, un token si risolve in un valore specifico, indipendentemente dall'elemento che lo contiene. Tuttavia, se il token è correlato a un pacchetto o una funzionalità, il valore del token dipende in cui è contenuto. Ad esempio, se è una funzionalità nel pacchetto, il token `$SharePoint.Package.Name$` risolve nel valore di "Pacchetto A." Se la stessa funzionalità è nel pacchetto B, quindi `$SharePoint.Package.Name$` si risolve in "Pacchetto B."  
  
## <a name="tokens-list"></a>Elenco di token  
 Nella tabella seguente sono elencati i token disponibili.  
  
|nome|Descrizione|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Il nome del file di progetto che lo contiene, ad esempio, "NewProj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Il nome del file di progetto contenitore senza l'estensione del nome file. Ad esempio, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Il nome visualizzato (nome sicuro) del contenitore progetto dell'assembly di output.|  
|$SharePoint.Project.AssemblyFileName$|Il nome del contenitore progetto dell'assembly di output.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Il nome del progetto contiene dell'assembly, senza l'estensione del nome file di output.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Assembly, convertito in una stringa di output del token di chiave pubblica del contenitore progetto. (16 caratteri in "x2" formato esadecimale.)|  
|$SharePoint.Package.Name$|Il nome del pacchetto contenitore.|  
|$SharePoint.Package.FileName$|Il nome del file di definizione del pacchetto contenitore.|  
|$SharePoint.Package.FileNameWithoutExtension$|Il nome del file di definizione del pacchetto contenitore (senza estensione).|  
|$SharePoint.Package.Id$|L'ID di SharePoint per il pacchetto che lo contiene. Se una funzionalità viene utilizzata in più di un pacchetto, questo valore verrà modificato.|  
|$SharePoint.Feature.FileName$|Il nome del file di definizione della funzionalità contenitore, ad esempio Feature1. feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Il nome del file di definizione di funzionalità, senza l'estensione del nome file.|  
|$SharePoint.Feature.DeploymentPath$|Il nome della cartella che contiene la funzionalità nel pacchetto. Questo token corrisponde alla proprietà "Percorso di distribuzione" nella finestra di progettazione di funzionalità. È un valore di esempio, "Project1_Feature1".|  
|$SharePoint.Feature.Id$|L'ID di SharePoint della funzionalità contenitore. Il token, come con tutti i token a livello di funzionalità, può essere utilizzato solo dai file inclusi in un pacchetto tramite una funzionalità, non aggiunto direttamente a un pacchetto all'esterno di una funzionalità.|  
|$SharePoint.ProjectItem.Name$|Il nome dell'elemento di progetto (non il nome del file) ottenuto da **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. $ AssemblyQualifiedName|Nome completo di assembly del tipo che corrisponde al [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. Il formato del [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] è minuscolo e corrisponde al formato Guid.ToString("D"), vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.|  
|$SharePoint.Type. \<GUID >. $ FullName|Il nome completo del tipo che corrisponde al GUID nel token. Il formato del GUID è minuscolo e corrisponde al formato GUID (vale a dire xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Aggiunta di estensioni per la sostituzione dei Token di elenco di estensioni di File  
 Anche se i token teoricamente possono essere utilizzati da qualsiasi file che appartiene a un progetto SharePoint elemento incluso nel pacchetto, per impostazione predefinita, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Cerca token solo nel file di pacchetto, i file manifesto e i file con le estensioni seguenti:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Web part  
  
-   DWP  
  
 Queste estensioni vengono definite per il `<TokenReplacementFileExtensions>` elemento nel file Microsoft. VisualStudio nel... \\< file di programma\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools cartella.  
  
 È tuttavia possibile aggiungere altre estensioni di file all'elenco. A tale scopo, aggiungere un `<TokenReplacementFileExtensions>` elemento a qualsiasi oggetto PropertyGroup nel file di progetto SharePoint definito prima il \<Import > del file di destinazioni di SharePoint.  
  
> [!NOTE]  
>  Poiché la sostituzione dei token si verifica dopo la compilazione di un progetto, è consigliabile non aggiungere estensioni di file per i tipi di file che vengono compilati, ad esempio con estensione cs, vb o. resx. I token vengono sostituiti solo nei file non compilati.  
  
 Ad esempio, per aggiungere le estensioni di nome file "myextension" e "yourextension" all'elenco di estensioni di file di sostituzione dei token, aggiungere quanto segue in un file con estensione csproj:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 In alternativa, è possibile aggiungere l'estensione direttamente al file con estensione targets. Tuttavia, questa operazione modifica l'elenco di estensioni per tutti i progetti SharePoint incluso nel pacchetto nel sistema locale, non solo la propria. È possibile pratico quando si è l'unico sviluppatore nel sistema o se richiedono la maggior parte dei progetti. Tuttavia, perché si tratta di specifiche del sistema, questo approccio non è molto portatile e di conseguenza, è consigliabile aggiungere tutte le estensioni il file di progetto invece.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  