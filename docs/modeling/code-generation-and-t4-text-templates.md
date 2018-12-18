---
title: Generazione di codice e modelli di testo T4 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 029b5264d5275458aee1893df0ba4dd4d83d1a91
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Generazione di codice e modelli di testo T4
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]un *modello di testo T4* è una combinazione di blocchi di testo e della logica di controllo che può generare un file di testo. La logica di controllo è scritta come frammenti di codice programma in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. In Visual Studio 2015 Update 2 e versioni successive è possibile usare le funzionalità di C# versione 6.0 nelle direttive dei modelli T4. Il file generato può essere testo di qualsiasi tipo, ad esempio una pagina Web, un file di risorse o codice sorgente di un programma in qualsiasi linguaggio.  
  
 Esistono due tipi di modelli di testo T4:  
  
 I**modelli di testo T4 in fase di esecuzione** (modelli "pre-elaborati") vengono eseguiti nell'applicazione per produrre stringhe di testo, in genere come parte dell'output.  
 È ad esempio possibile creare un modello per definire una pagina HTML:  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 Si noti che il modello è simile all'output generato. La somiglianza del modello all'output risultante consente di evitare errori quando lo si vuole modificare.  
  
 Inoltre, il modello contiene frammenti di codice programma. È possibile usare questi frammenti per ripetere sezioni di testo, creare sezioni condizionali e visualizzare dati dell'applicazione.  
  
 Per generare l'output, l'applicazione chiama una funzione che viene generata dal modello. Ad esempio:  
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 L'applicazione può essere eseguita in un computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 Per creare un modello in fase di esecuzione, aggiungere un file di **modello di testo pre-elaborato** al progetto. In alternativa, è possibile aggiungere un file di testo normale e impostare la relativa proprietà **Strumento personalizzato** su **TextTemplatingFilePreprocessor**.  
  
 Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Per ulteriori informazioni sulla sintassi dei modelli, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
 I**modelli di testo T4 in fase di progettazione** vengono eseguiti in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per definire parte del codice sorgente e altre risorse dell'applicazione.  
 In genere si usano diversi modelli che leggono i dati in un singolo file di input o un database e si generano alcuni file `.cs`, `.vb`o altri file di origine. Ogni modello genera un file. Vengono eseguiti in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 I dati di input potrebbero ad esempio essere un file XML di dati di configurazione. Ogni volta che si modifica il file XML durante lo sviluppo, i modelli di testo rigenereranno parte del codice dell'applicazione. Uno dei modelli potrebbe assomigliare all'esempio seguente:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 A seconda dei valori nel file XML, il file `.cs` generato sarà simile al seguente:  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 Facendo un altro esempio, l'input potrebbe essere un diagramma di flusso di lavoro in un'attività aziendale. Quando gli utenti modificano il flusso di lavoro aziendale o quando si inizia a lavorare con nuovi utenti che dispongono di un flusso di lavoro diverso, è facile rigenerare il codice per adattarlo al nuovo modello.  
  
 I modelli in fase di progettazione rendono più veloce e affidabile la modifica della configurazione quando cambiano i requisiti. In genere l'input è definito in termini di requisiti aziendali, come illustrato nell'esempio del flusso di lavoro. Questo rende più semplice discutere le modifiche con gli utenti. I modelli in fase di progettazione sono pertanto un utile strumento in un processo di sviluppo agile.  
  
 Per creare un modello in fase di progettazione, aggiungere un file di **modello di testo** al progetto. In alternativa, è possibile aggiungere un file di testo normale e impostare la relativa proprietà **Strumento personalizzato** su **TextTemplatingFileGenerator**.  
  
 Per ulteriori informazioni, vedere [generazione codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Per ulteriori informazioni sulla sintassi dei modelli, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Il termine *modello* talvolta viene usato per descrivere i dati letti da uno o più modelli. Il modello può avere qualsiasi formato, in qualsiasi tipo di file o database. Non deve essere un modello UML o un modello di linguaggio specifico di dominio. "Modello" indica semplicemente che i dati possono essere definiti in termini di concetti aziendali, invece di essere simili al codice.  
  
 La funzionalità di trasformazione del modello di testo è denominata *T4*.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 In qualsiasi applicazione che genera file di testo, i modelli di testo precompilati rappresentano un metodo semplice e affidabile per definire il testo. Questo metodo non può tuttavia essere usato per i modelli di testo che cambiano in fase di esecuzione.  
  
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 La generazione di codice e di altre risorse da un modello consente di aggiornare l'applicazione attraverso l'aggiornamento del modello.  
  
 [Generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md)  
 Se è stato installato l'SDK di visualizzazione e modellazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , è possibile garantire il software generato resti aggiornato con le modifiche nel modello.  
  
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)  
 La sintassi di un file di modello di testo.  
  
 [Procedura dettagliata: generazione di codice tramite modelli di testo](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Una dimostrazione di un modo per usare la generazione di codice.  
  
 [Debug di un modello di testo T4](../modeling/debugging-a-t4-text-template.md)  
 Come eseguire il debug dei modelli di testo e alcuni errori comuni relativi ai modelli di testo.  
  
 [Generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Lo strumento della riga di comando che è possibile usare per eseguire trasformazioni dei modelli di testo.  
  
 [Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)  
 Come scrivere processori di direttive e host di modelli personalizzati per le proprie origini dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)