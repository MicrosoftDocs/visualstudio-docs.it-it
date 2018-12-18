---
title: Personalizzare la compilazione | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5b11acd4360aa86d4727a4c697a56eaa753d522c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customize-your-build"></a>Personalizzare la compilazione
Nelle versioni di MS Build precedenti alla versione 15, per specificare una nuova proprietà personalizzata per i progetti nella soluzione, è necessario aggiungere manualmente un riferimento a tale proprietà per ogni file di progetto della soluzione. Oppure, è necessario definire la proprietà in un file *PROPS* e quindi importare in modo esplicito il file *PROPS* in ogni progetto della soluzione, tra le altre cose.

Tuttavia, ora è possibile aggiungere una nuova proprietà a ogni progetto in un unico passaggio, definendola in un singolo file denominato *Directory.Build.props* nella radice del repository. Quando si esegue MSBuild, *Microsoft.Common.props* cerca la struttura di directory per il file *Directory.Build.props* (e *MicrosoftCommon.targets* cerca *Directory.Build.targets*). Se trova la struttura, importa la proprietà. *Directory.Build.props* è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory.

## <a name="directorybuildprops-example"></a>Esempio di Directory.Build.props
Ad esempio, per consentire a tutti i progetti di accedere alla nuova funzionalità di Roslyn **/deterministic** (esposta nella destinazione `CoreCompile` di Roslyn dalla proprietà `$(Deterministic)`), è possibile eseguire le operazioni indicate di seguito.

1. Creare un nuovo file nella radice del repository denominato *Directory.Build.props*.
2. Aggiungere al file il seguente codice XML.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Eseguire MSBuild. Le importazioni esistenti del progetto di *Microsoft.Common.props* e *Microsoft.Common.targets* trovano il file e lo importano.

## <a name="search-scope"></a>Ambito di ricerca
Quando cerca un file *Directory.Build.props*, MSBuild scorre la struttura di directory verso l'alto a partire dalla posizione del progetto (`$(MSBuildProjectFullPath)`), fermandosi quando individua un file *Directory.Build.props*. Ad esempio, se `$(MSBuildProjectFullPath)` è *c:\users\nomeutente\code\test\case1*, MSBuild inizia a cercare da quel punto ed esegue la ricerca nella struttura di directory verso l'alto finché non trova un file *Directory.Build.props*, come nella struttura di directory riportata di seguito.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
La posizione del file della soluzione è irrilevante per *Directory.Build.props*.

## <a name="import-order"></a>Ordine di importazione

*Directory.Build.props* viene importato molto presto in *Microsoft.Common.props*, quindi le proprietà definite in un secondo tempo non sono disponibili per questo file. Quindi, evitare di fare riferimento a proprietà che non sono ancora state definite (e che verranno restituite come vuote).

*Directory.Build.targets* viene importato da *Microsoft.Common.targets* dopo l'importazione dei file *.targets* dai pacchetti NuGet. Può quindi essere usato per eseguire l'override di proprietà e destinazioni definite nella maggior parte della logica di compilazione, ma in alcuni casi può essere necessario eseguire personalizzazioni all'interno del file di progetto dopo l'importazione finale.

## <a name="use-case-multi-level-merging"></a>Caso d'uso: unione a più livelli

Si supponga di avere questa struttura della soluzione standard:

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

Potrebbe essere preferibile usare proprietà comuni per tutti i progetti *(1)*, proprietà comuni per i progetti *src* *(2-src)* e proprietà comuni per i progetti *test* *(2-test)*.

Per consentire a MSBuild di unire correttamente i file "interni"(*2-src* e *2-test*) e il file "esterno" (*1*), è necessario tenere presente che quando MSBuild trova un file *Directory.Build.props*, interrompe l'analisi. Per continuare l'analisi e completare l'unione con il file esterno, inserire il file in entrambi i file interni:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

L'approccio generale di MSBuild può essere riepilogato come segue:

- Per ogni progetto, MSBuild trova il primo file *Directory.Build.props* procedendo verso l'alto nella struttura della soluzione, lo unisce ai valori predefiniti e interrompe l'analisi
- Se si vogliono rilevare e unire più livelli, usare [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (illustrato in precedenza) per importare il file "esterno" dal file "interno"
- Se il file "esterno" non importa a sua volta un elemento situato a un livello superiore, l'analisi si interrompe qui
- Per controllare il processo di analisi/unione, usare `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`

O più semplicemente: il primo file *Directory.Build.props* che non esegue alcuna importazione è il punto in cui MSBuild si arresta.

## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
