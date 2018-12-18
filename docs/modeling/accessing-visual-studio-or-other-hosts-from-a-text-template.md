---
title: Accesso a Visual Studio o altri host da un modello di testo
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 171b3d3060ea00cc5adc9ca1220cb86148f8d883
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Accedere a Visual Studio o altri host da un modello di testo

In un modello di testo, è possibile utilizzare metodi e proprietà che vengono esposti dall'host che esegue il modello. Visual Studio è un esempio di un host.

> [!NOTE]
> È possibile utilizzare i metodi di host e le proprietà nei modelli di testo normale, ma non nelle *pre-elaborato* modelli di testo.

## <a name="obtain-access-to-the-host"></a>Ottenere l'accesso all'host

Per accedere all'host, impostare `hostspecific="true"` nella `template` direttiva. È ora possibile usare `this.Host`, che presenta tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Il <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> tipo dispone di membri che è possibile utilizzare, ad esempio, per risolvere i nomi di file e registrare gli errori.

### <a name="resolve-file-names"></a>Risolvere i nomi di File

Per trovare il percorso completo di un file relativo al modello di testo, usare `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Visualizzare i messaggi di errore

In questo esempio Registra i messaggi quando si trasforma il modello. Se l'host è Visual Studio, gli errori vengono aggiunti per il **elenco errori**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Utilizzare l'API di Visual Studio

Se si sta eseguendo un modello di testo in Visual Studio, è possibile utilizzare `this.Host` per accedere ai servizi forniti da Visual Studio e i pacchetti o le estensioni caricate.

Impostare hostspecific = "true", quindi eseguire il cast `this.Host` a <xref:System.IServiceProvider>.

Questo esempio mostra come ottenere API di Visual Studio, <xref:EnvDTE.DTE>, come un servizio:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Utilizzo dell'ereditarietà del modello hostSpecific

Specificare `hostspecific="trueFromBase"` se si utilizza anche il `inherits` attributo, e se si eredita da un modello che specifica `hostspecific="true"`. In caso contrario, è possibile che venga visualizzato un avviso che del compilatore la proprietà `Host` è stata dichiarata due volte.