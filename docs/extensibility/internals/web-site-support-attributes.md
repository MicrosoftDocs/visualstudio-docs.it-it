---
title: Sito Web supporto attributi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-attributes"></a>Sito Web supporto attributi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Progetto di sito Web può essere esteso per fornire il supporto per il Web, linguaggi di programmazione. Il linguaggio deve registrarsi con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che i modelli di progetto possono essere visualizzati nel **nuovo sito Web** la finestra di dialogo quando si seleziona la lingua.

L'esempio di IronPython Studio include il supporto del sito web. L'esempio contiene le seguenti classi di attributi per registrare IronPython come lingua codebehind per nuovi progetti Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Questo attributo viene posizionato sul progetto di linguaggio. La lingua viene aggiunto all'elenco dei linguaggi di programmazione Web di **Language** nell'elenco di **nuovo sito Web** la finestra di dialogo. Ad esempio, il codice seguente aggiunge IronPython all'elenco:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Questo attributo imposta inoltre il percorso di modelli per scegliere la cartella dei modelli. Per ulteriori informazioni sulla posizione della cartella modelli, vedere [modelli di sito Web supporto](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Questo attributo viene posizionato sul progetto di linguaggio. Consente il progetto di sito Web annidare un tipo di file (correlato) in un altro tipo di file (principale) nei **Esplora**.

 Ad esempio, il codice seguente specifica che un file codebehind IronPython è correlato a un file con estensione aspx. Quando in una soluzione di sito Web di IronPython, viene creata una nuova pagina Web aspx, un nuovo file di origine. py viene generato e visualizzato come nodo figlio della pagina. aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Seleziona il provider di IntelliSense per la lingua.

 Ad esempio, il codice seguente specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, devono essere creati su richiesta per fornire servizi di linguaggio.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L'implementazione di IVsIntellisenseProject gestisce riferimenti e il compilatore di linguaggio viene chiamato quando una pagina Web con il codice viene richiesta ma non è memorizzato nella cache.

## <a name="see-also"></a>Vedere anche
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)