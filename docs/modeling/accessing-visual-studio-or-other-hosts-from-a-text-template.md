---
title: Accesso a Visual Studio o altri host da un modello di testo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cd72a2838e9dd7a903e5cf76aac30e2922708872
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Accesso a Visual Studio o altri host da un modello di testo
In un modello di testo, è possibile utilizzare i metodi e proprietà esposte dall'host che esegue il modello, ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Si applica ai modelli di testo normale, modelli di testo non pre-elaborato.  
  
## <a name="obtaining-access-to-the-host"></a>Ottenere l'accesso all'host  
 Impostare `hostspecific="true"` nel `template` direttiva. Consente di utilizzare `this.Host`, di tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Questo tipo dispone di membri che è possibile, ad esempio, utilizzare per risolvere i nomi di file e registrare gli errori.  
  
### <a name="resolving-file-names"></a>Risoluzione dei nomi di File  
 Per trovare il percorso completo di un file relativo al modello di testo, utilizzare la. Host.ResolvePath().  
  
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
  
### <a name="displaying-error-messages"></a>Visualizzazione di messaggi di errore  
 In questo esempio Registra i messaggi quando si trasforma il modello. Se l'host è [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vengono aggiunti alla finestra di errore.  
  
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
  
## <a name="using-the-visual-studio-api"></a>Utilizzo dell'API di Visual Studio  
 Se si sta eseguendo un modello di testo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile utilizzare `this.Host` per accedere ai servizi forniti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ed eventuali pacchetti o le estensioni caricate.  
  
 Impostare hostspecific = "true", quindi eseguire il cast `this.Host` a <xref:System.IServiceProvider>.  
  
 Questo esempio mostra come ottenere il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, come un servizio:  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>Utilizzo di hostSpecific con ereditarietà modello  
 Specificare `hostspecific="trueFromBase"` se si utilizza anche il `inherits` attributo, e se si eredita da un modello che specifica `hostspecific="true"`. Ciò consente di evitare un avviso del compilatore l'effetto che la proprietà `Host` è stata dichiarata due volte.