---
title: 'Procedura: Visualizzare un elenco di elementi separati da virgole | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 10ff36702f4fba2ed5093e866ac57a099fbbc904
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081810"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Procedura: Visualizzare un elenco di elementi separati da virgole
Quando si usano gli elementi elencati in [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), è talvolta utile visualizzare il contenuto di tali elenchi di elementi in un modo facilmente leggibile. In alternativa, si potrebbe usare un attività che accetta un elenco di elementi separati da una stringa di separazione speciale. In entrambi i casi, è possibile specificare una stringa di separazione per un elenco di elementi.  
  
## <a name="separate-items-in-a-list-with-commas"></a>Separare gli elementi in un elenco con virgole  
 Per impostazione predefinita, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa i punti e virgola per separare gli elementi in un elenco. Si consideri ad esempio un elemento `Message` con il valore seguente:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Quando l'elenco di elementi `@(TXTFile)` contiene gli elementi *App1.txt*, *App2.txt* e *App3.txt*, il messaggio è:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Se si vuole modificare il comportamento predefinito, è possibile specificare un separatore personalizzato. La sintassi per specificare un separatore per un elenco di elementi è:  
  
 `@(ItemListName, '<separator>')`  
  
 Il separatore può essere un singolo carattere o una stringa e deve essere racchiuso tra virgolette singole.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Per inserire una virgola e uno spazio tra gli elementi  
  
-   Usare una notazione simile alla seguente:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Esempio  
 In questo esempio l'attività [Exec](../msbuild/exec-task.md) esegue lo strumento findstr per trovare le stringhe di testo specificate nel file *Phrases.txt*. Nel comando findstr le stringhe di ricerca letterali sono indicate dall'opzione **/c:**, pertanto il separatore di elementi `/c:` viene inserito tra gli elementi nell'elenco di elementi `@(Phrase)`.  
  
 Per questo esempio, la riga di comando equivalente è:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Elementi](../msbuild/msbuild-items.md)