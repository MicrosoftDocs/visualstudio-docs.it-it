---
title: 'Procedura: Ignorare gli errori nelle attività | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild - "vs-ide-sdk"
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: 348a026815d0d48390fed5741e6dba741fda9937
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-ignore-errors-in-tasks"></a>Procedura: Ignorare gli errori nelle attività
A volte è necessario che una compilazione sia a tolleranza di errore in determinate attività. Se tali attività non critiche hanno esito negativo, si vuole che la compilazione prosegua perché può ugualmente produrre l'output necessario. Se, ad esempio, un progetto usa un'attività `SendMail` per inviare un messaggio di posta elettronica dopo che ogni componente è stato compilato, si può considerare accettabile che la compilazione continui fino al completamento anche quando i server di posta non sono disponibili e i messaggi di stato non possono essere inviati. O anche, ad esempio, se di solito i file intermedi vengono eliminati durante la compilazione, si può considerare accettabile che la compilazione continui fino al completamento anche quando tali file non possono essere eliminati.  
  
## <a name="using-the-continueonerror-attribute"></a>Uso dell'attributo ContinueOnError  
 L'attributo `ContinueOnError` dell'elemento `Task` controlla se una compilazione si arresta o continua quando si verifica un errore dell'attività. Questo attributo controlla anche se gli errori vengono considerati errori o avvisi quando la compilazione continua.  
  
 L'attributo `ContinueOnError` può contenere uno dei valori seguenti:  
  
-   **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.  
  
-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.  
  
-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.  
  
 Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.  
  
 Il valore predefinito di `ContinueOnError` è `ErrorAndStop`. Se si imposta l'attributo su `ErrorAndStop`, il comportamento diventa esplicito per chiunque legga il file di progetto.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Per ignorare un errore in un'attività  
  
-   Usare l'attributo `ContinueOnError` dell'attività. Ad esempio:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente mostra che la destinazione `Build` è ancora in esecuzione e che la compilazione è considerata riuscita, anche se l'attività `Delete` ha esito negativo.  
  
```xml  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche
[MSBuild](../msbuild/msbuild.md)  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)