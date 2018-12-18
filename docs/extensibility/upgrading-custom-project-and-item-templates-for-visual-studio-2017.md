---
title: Aggiornamento progetto personalizzato e i modelli di Visual Studio 2017 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c0843c8bfb899dc23bcb1ce31eb3f8b9eaffd54
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Aggiornamento progetto personalizzato e i modelli di Visual Studio 2017

A partire da Visual Studio 2017, Visual Studio consente di individuare modelli di progetto e di elementi che sono stati installati da un'estensione VSIX o un file con estensione msi in modo diverso per le versioni precedenti di Visual Studio. Se si dispone di estensioni che utilizzano modelli di elemento o di progetto personalizzato, è necessario aggiornare le estensioni. Questo argomento illustra le operazioni da eseguire.

Questa modifica interessa solo Visual Studio 2017. Non si applica alle versioni precedenti di Visual Studio.

Se si desidera creare un modello di progetto o un elemento come parte di un'estensione VSIX, vedere [creazione Custom Project and Item Templates](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Modello di analisi

Nelle versioni precedenti di Visual Studio, **devenv /setup** o **devenv /installvstemplates** analizzati nel disco locale per trovare i modelli di progetto e di elemento. A partire da Visual Studio 2017, l'analisi viene eseguita solo per il percorso a livello di utente. Il percorso a livello di utente predefinito è **%USERPROFILE%\Documents\\< versione di Visual Studio\>\Templates\\**. Questo percorso viene utilizzato per i modelli generati dal **progetto** > **Esporta modelli...**  comando, se il **Importa automaticamente il modello in Visual Studio** opzione è selezionata nella procedura guidata.

Per altre posizioni (non dell'utente), è necessario includere un file manifest(.vstman) che specifica il percorso e altre caratteristiche del modello. Viene generato il file di .vstman insieme al file con estensione vstemplate utilizzato per i modelli. Se si installa l'estensione con un'estensione VSIX, è possibile eseguire ricompilando l'estensione in Visual Studio 2017. Ma se si utilizza un file con estensione msi, è necessario apportare le modifiche manualmente. Per un elenco di ciò che occorre per apportare queste modifiche, vedere **aggiornamenti per estensioni installate con un. MSI** più avanti in questo argomento.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con modelli di elemento o di progetto  

1.  Aprire la soluzione in Visual Studio 2017. Verrà richiesto di aggiornare il codice. Fare clic su **OK**.  
  
2.  Al termine dell'aggiornamento, si potrebbe essere necessario modificare la versione dell'installazione di destinazione. Nel progetto VSIX, aprire il file vsixmanifest e selezionare il **destinazioni di installazione** scheda. Se il **intervallo di versioni** campo **[14.0]**, fare clic su **modifica** e modificare in modo da includere 2017 di Visual Studio. Ad esempio, è possibile impostare **[14.0,15.0]** per installare l'estensione di Visual Studio 2015 o Visual Studio 2017, o di **[15.0]** installarla solo Visual Studio 2017.  
  
3.  Ricompilare il codice.  
  
4.  Chiudere Visual Studio.  
  
5.  Installare l'estensione VSIX.  
  
6.  È possibile testare l'aggiornamento nel modo seguente:  
  
    1.  Il file di analisi delle modifiche è attivato dalla chiave del Registro di sistema seguente:  
  
         **REG aggiungere hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Dopo aver aggiunto la chiave, eseguire **devenv /installvstemplates**.  
  
    3.  Riaprire Visual Studio. Il modello si trova nel percorso previsto.  
  
    > [!NOTE]
    >  I modelli di progetto di estensibilità di Visual Studio non sono disponibili quando la chiave del Registro di sistema è presente. È necessario eliminare la chiave del Registro di sistema (e rieseguire **devenv /installvstemplates**) come utilizzarli.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri suggerimenti per la distribuzione di progetto e modelli di elementi  
  
-   Evitare di utilizzare i file di modello ZIP. Compresso i file devono essere compressi per recuperare le risorse e il contenuto di modello, pertanto saranno costlier da utilizzare. In alternativa, è necessario distribuire i modelli di progetto e di elemento come singoli file nella propria directory per velocizzare l'inizializzazione di modello. Per le estensioni VSIX, attività di compilazione SDK verrà decomprimere automaticamente qualsiasi modello compresso durante la creazione del file VSIX.  
  
-   Evitare di usare voci di ID di pacchetto o risorse per il nome del modello, descrizione, icona o anteprima per evitare i caricamenti di assembly di risorse non necessari durante l'individuazione di modello. In alternativa, è possibile utilizzare manifesti localizzati per creare una voce di modello per ognuna delle impostazioni locali, che Usa nomi localizzati o proprietà.  
  
-   Se si desidera includere modelli come elementi del file, la generazione del manifesto potrebbe non fornire i risultati previsti. In tal caso, è necessario aggiungere un manifesto generato manualmente al progetto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modifiche ai file nel progetto e modelli di elemento  
Vengono illustrati i punti di differenza tra Visual Studio 2015 e versioni di Visual Studio 2017 dei file di modello, in modo che è possibile creare nuovi file correttamente.  
  
 Ecco il file. vstemplate di progetto predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file .vstman (sarà possibile trovarlo nella directory del manifesto del progetto VSIX) che causa la ricompilazione del progetto VSIX:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite dal [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento rimane invariato. Il  **\<VSTemplateContainer >** elemento punta al file con estensione vstemplate per il modello associato.  
  
 Ecco il file. vstemplate elemento predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file .vstman (sarà possibile trovarlo nella directory del manifesto del progetto VSIX) che causa la ricompilazione del progetto VSIX:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite dal  **\<TemplateData >** elemento rimane invariato. Il  **\<VSTemplateContainer >** elemento punta al file con estensione vstemplate per il modello associato  
  
 Per ulteriori informazioni sui diversi elementi del file .vstman, vedere [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Gli aggiornamenti per le estensioni installate con un. FILE MSI

Alcune estensioni basate su MSI distribuire modelli in posizioni di modelli comuni, ad esempio le operazioni seguenti:

- **\<Directory di installazione di Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**

- **\<Directory di installazione di Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< progetto/ItemTemplates >**

Se l'estensione esegue una distribuzione basata su MSI, è necessario generare manualmente il manifesto di modello e assicurarsi che sia inclusa nel programma di installazione di estensione. Confrontare gli esempi di .vstman sopra elencati e [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

È consigliabile creare manifesti distinti per i modelli di progetto e di elemento e puntano modello directory radice come specificato sopra. Creare un manifesto per l'estensione e le impostazioni locali.

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi di individuazione di modello](troubleshooting-template-discovery.md)  
[Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)