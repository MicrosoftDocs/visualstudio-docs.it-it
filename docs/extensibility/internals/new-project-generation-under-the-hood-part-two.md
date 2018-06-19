---
title: 'Nuova generazione del progetto: Dietro le quinte, parte 2 | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69174be20a0961a6074650471bcb4b9d1df9fa98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133189"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nuova generazione del progetto: Dietro le quinte, parte 2
In [nuova generazione progetto: in parte integrante, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) abbiamo visto come **nuovo progetto** inserite nella finestra di dialogo. Si supponga di aver selezionato un **applicazione Windows di Visual c#**, compilati il **nome** e **percorso** caselle di testo e si fa clic su OK.  
  
## <a name="generating-the-solution-files"></a>Generazione dei file di soluzione  
 Scelta di un modello di applicazione indirizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per decomprimere e aprire il file con estensione vstemplate corrispondente e per avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.  
  
 Il modello decomprime il file di origine, denominato modelli di elementi, dalla stessa cartella con estensione zip che contiene il file. vstemplate. Il modello consente di copiare questi file al nuovo progetto, di conseguenza la personalizzazione.  
  
### <a name="template-parameter-replacement"></a>Sostituzione dei parametri di modello  
 Quando il modello di copia di un modello di elemento a un nuovo progetto, eventuali parametri di modello vengono sostituite con le stringhe per personalizzare il file. Un parametro di modello è un token speciale che è preceduto e seguito da un segno di dollaro, ad esempio, $ $date.  
  
 Esaminiamo un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Programmi\Microsoft Visual Studio.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Se si crea un nuovo progetto applicazione Windows denominato "semplice", il modello sostituisce la `$safeprojectname$` parametro con il nome del progetto.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Un aspetto all'interno di una. File VSTemplate  
 Il formato è un file. vstemplate di base  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 È stato esaminato il \<TemplateData > sezione di [nuova generazione progetto: in parte integrante, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione consentono di controllare l'aspetto del **nuovo progetto** la finestra di dialogo.  
  
 I tag di \<TemplateContent > sezione la generazione di nuovi progetti ed elementi di progetto di controllo. Ecco il \<TemplateContent > sezione dal file nella cartella \Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip cswindowsapplication.vstemplate.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 Il \<progetto > tag controlla la generazione di un progetto e \<ProjectItem > tag controlla la generazione di un elemento di progetto. Se il parametro ReplaceParameters è true, il modello verrà personalizzare tutti i parametri di modello nel file di progetto o elemento. In questo caso, tutti gli elementi di progetto personalizzati, ad eccezione di Settings. Settings.  
  
 Il parametro TargetFileName specifica il nome e percorso relativo del file di progetto risultante o dell'elemento. Ciò consente di creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento del progetto avrà lo stesso nome di modello di elemento di progetto.  
  
 La struttura di cartelle dell'applicazione Windows risulta è simile al seguente:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Il primo e unico \<progetto > tag in legge il modello:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Questo indica il modello di progetto per creare il file di progetto Simple.csproj copiando e personalizzazione di windowsapplication.csproj di elemento di modello.  
  
### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti  
 È possibile visualizzare in Esplora soluzioni, che la cartella di proprietà è presente e che contiene i file previsti. Ma cosa succede progetto fa riferimento e dipendenze di file di progettazione, ad esempio Resources.Designer.cs per Resources. resx e Form1. Designer.cs a Form1. cs?  Questi vengono impostati nel file Simple.csproj quando viene generato.  
  
 Ecco il \<ItemGroup > da Simple.csproj che crea i riferimenti al progetto:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 È possibile visualizzare sono i riferimenti al sei progetto che vengono visualizzati in Esplora soluzioni. Ecco una sezione da un altro \<ItemGroup >. Numero di righe di codice sia stata eliminata per maggiore chiarezza. In questa sezione rende Settings.Designer.cs dipendente Settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di un nuovo progetto: dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)