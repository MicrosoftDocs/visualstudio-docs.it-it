---
title: Scrittura di attività | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c08fcc8baa0e892678cc376056a35c0f09101f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="task-writing"></a>Scrittura di attività
Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Le attività sono contenute nelle destinazioni. In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è inclusa una raccolta di attività tipiche ed è anche possibile creare le proprie attività. Per altre informazioni sulla raccolta di attività inclusa in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere il [riferimento alle attività](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Attività  
 Alcuni esempi di attività sono [Copy](../msbuild/copy-task.md), per eseguire la copia di uno o più file, [MakeDir](../msbuild/makedir-task.md), per creare una directory e [Csc](../msbuild/csc-task.md), per compilare i file di codice sorgente di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Ogni attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nell'assembly Microsoft.Build.Framework.dll.  
  
 È possibile implementare un'attività in due modi:  
  
-   Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>, definita nell'assembly Microsoft.Build.Utilities.dll. L'attività implementa ITask e specifica le implementazioni predefinite di alcuni membri di ITask. Inoltre, la registrazione è più semplice.  
  
 In entrambi i casi è necessario aggiungere alla classe un metodo denominato `Execute`, ovvero il metodo che viene chiamato quando l'attività è in esecuzione. Questo metodo non accetta parametri e restituisce un valore `Boolean`: `true` se l'attività ha avuto esito positivo o `false` se ha avuto esito negativo. Nell'esempio seguente viene illustrata un'attività che non esegue alcuna azione e restituisce `true`.  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Il file di progetto seguente esegue questa attività:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Durante l'esecuzione, le attività possono anche ricevere input dal file di progetto se si creano proprietà .NET per la classe dell'attività. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] imposta queste proprietà immediatamente prima di chiamare il metodo `Execute` dell'attività. Per creare una proprietà stringa, usare il codice dell'attività, ad esempio:  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Il seguente file di progetto esegue questa attività e imposta `MyProperty` sul valore specificato:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Registrazione di attività  
 Se un progetto sta per eseguire un'attività, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve sapere come individuare l'assembly che contiene la classe dell'attività. Le attività vengono registrate usando l'[elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 Il file Microsoft.Common.Tasks di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è un file di progetto contenente un elenco di elementi `UsingTask` che registrano tutte le attività disponibili con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Questo file è incluso automaticamente durante la compilazione di ogni progetto. Se un'attività registrata in Microsoft,Common.Tasks è registrata anche nel file di progetto corrente, il file di progetto corrente ha la precedenza, ovvero è possibile sostituire un'attività predefinita con un'attività personalizzata con lo stesso nome.  
  
> [!TIP]
>  È possibile visualizzare un elenco delle attività disponibili con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] visualizzando il contenuto di Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Generazione di eventi da un'attività  
 Se l'attività deriva dalla classe helper <xref:Microsoft.Build.Utilities.Task>, è possibile usare uno qualsiasi dei seguenti metodi helper per la classe <xref:Microsoft.Build.Utilities.Task> per generare eventi che verranno intercettati e visualizzati da tutti i logger registrati:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Se l'attività implementa <xref:Microsoft.Build.Framework.ITask> direttamente, è comunque possibile generare tali eventi, ma è necessario usare l'interfaccia IBuildEngine. Nell'esempio seguente viene illustrata un'attività che implementa ITask e genera un evento personalizzato:  
  
```csharp
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>Richiesta dell'impostazione dei parametri dell'attività  
 È possibile contrassegnare determinate proprietà dell'attività come "obbligatorie" in modo che i file di progetto che eseguono l'attività siano obbligati a impostare valori per queste proprietà altrimenti la compilazione non riesce. Applicare l'attributo `[Required]` alla proprietà .NET nell'attività come segue:  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 L'attributo `[Required]` è definito da <xref:Microsoft.Build.Framework.RequiredAttribute> nello spazio dei nomi <xref:Microsoft.Build.Framework>.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 La seguente classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] rappresenta un'attività derivata dalla classe helper <xref:Microsoft.Build.Utilities.Task>. L'attività restituisce `true`, che indica che ha avuto esito positivo.  
  
### <a name="code"></a>Codice  
  
```csharp
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 La seguente classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] rappresenta un'attività che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>. L'attività restituisce `true`, che indica che ha avuto esito positivo.  
  
### <a name="code"></a>Codice  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 Questa classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] rappresenta un'attività derivata dalla classe helper <xref:Microsoft.Build.Utilities.Task>. Ha una proprietà stringa obbligatoria e genera un evento che viene visualizzato da tutti i logger registrati.  
  
### <a name="code"></a>Codice  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra un file di progetto che richiama l'attività dell'esempio precedente, SimpleTask3.  
  
### <a name="code"></a>Codice  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)