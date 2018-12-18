---
title: Attività inline di MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39bc1acd059c9a915f330c74140c89d5f4fa40ff
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-inline-tasks"></a>Attività inline di MSBuild
Le attività di MSBuild in genere vengono create compilando una classe che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).  
  
 A partire dalla versione 4 di .NET Framework è possibile creare attività inline nel file di progetto. Non è necessario creare un assembly separato per ospitare l'attività. In questo modo è più semplice tenere traccia del codice sorgente e distribuire l'attività. Il codice sorgente è integrato nello script.  
  
## <a name="the-structure-of-an-inline-task"></a>Struttura di un'attività inline  
 Un'attività inline è contenuta in un elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). L'attività inline e l'elemento `UsingTask` che la contiene in genere sono inclusi in un file TARGETS e vengono importati in altri file di progetto in base alle esigenze. Di seguito è riportata un'attività inline di base. Si noti che non esegue alcuna operazione.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 L'elemento `UsingTask` nell'esempio ha tre attributi che descrivono l'attività e la factory dell'attività inline che la compila.  
  
-   L'attributo `TaskName` assegna un nome all'attività, in questo caso `DoNothing`.  
  
-   L'attributo `TaskFactory` assegna un nome alla classe che implementa la factory dell'attività inline.  
  
-   L'attributo `AssemblyFile` assegna la posizione della factory dell'attività inline. In alternativa, è possibile usare l'attributo `AssemblyName` per specificare il nome completo della classe factory dell'attività inline, che in genere si trova nella Global Assembly Cache (GAC).  
  
 Gli elementi rimanenti dell'attività `DoNothing` sono vuoti e vengono specificati per illustrare l'ordine e la struttura di un'attività inline. Un esempio più concreto è riportato più avanti in questo argomento.  
  
-   L'elemento `ParameterGroup` è facoltativo. Se specificato, consente di dichiarare i parametri per l'attività. Per altre informazioni sui parametri di input e output, vedere "Parametri di input e output" più avanti in questo argomento.  
  
-   L'elemento `Task` descrive e contiene il codice sorgente dell'attività.  
  
-   L'elemento `Reference` specifica i riferimenti agli assembly .NET usati nel codice. Equivale all'aggiunta di un riferimento a un progetto in Visual Studio. L'attributo `Include` specifica il percorso dell'assembly di riferimento.  
  
-   L'elemento `Using` indica gli spazi dei nomi a cui si vuole accedere. Ricorda l'istruzione `Using` in Visual C#. L'attributo `Namespace` specifica lo spazio dei nomi da includere.  
  
 Gli elementi `Reference` e `Using` sono indipendenti dal linguaggio di programmazione. Le attività inline possono essere scritte in uno dei linguaggi .NET CodeDOM supportati, ad esempio Visual Basic, Visual C#.  
  
> [!NOTE]
>  Gli elementi contenuti in `Task` sono specifici della factory dell'attività, in questo caso la factory dell'attività del codice.  
  
### <a name="code-element"></a>Elemento Code  
 L'ultimo elemento figlio visualizzato all'interno dell'elemento `Task` è l'elemento `Code`. L'elemento `Code` contiene o individua il codice che deve essere compilato in un'attività. Ciò che si inserisce nell'elemento `Code` dipende da come si vuole scrivere l'attività.  
  
 L'attributo `Language` specifica il linguaggio di programmazione in cui è scritto il codice. I valori accettabili sono `cs` per C#, `vb` per Visual Basic.  
  
 L'attributo `Type` specifica il tipo di codice rilevato nell'elemento `Code`.  
  
-   Se il valore di `Type` è `Class`, l'elemento `Code` contiene il codice per una classe che deriva dall'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Se il valore di `Type` è `Method`, il codice definisce un override del metodo `Execute` dell'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Se il valore di `Type` è `Fragment`, il codice definisce il contenuto del metodo `Execute` ma non la firma o l'istruzione `return`.  
  
 Il codice in genere è visualizzato tra un indicatore `<![CDATA[` e un indicatore `]]>`. Poiché il codice è in una sezione CDATA, non è necessario preoccuparsi di eseguire l'escape di caratteri riservati, ad esempio "\<" o ">".  
  
 In alternativa, è possibile usare l'attributo `Source` dell'elemento `Code` per specificare il percorso di un file che contiene il codice per l'attività. Il codice nel file di origine deve essere del tipo specificato dall'attributo `Type`. Se l'attributo `Source` è presente, il valore predefinito di `Type` è `Class`. Se `Source` non è presente, il valore predefinito è `Fragment`.  
  
> [!NOTE]
>  Quando si definisce la classe dell'attività nel file di origine il nome della classe deve concordare con l'attributo `TaskName` dell'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md) corrispondente.  
  
## <a name="hello-world"></a>Hello World  
 Di seguito è riportata un'attività inline più concreta. L'attività HelloWorld visualizza "Hello, world!" nel dispositivo di registrazione degli errori predefinito, in genere la console del sistema o la finestra **Output** di Visual Studio. L'elemento `Reference` dell'esempio è incluso solo ai fini della spiegazione.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 È possibile salvare l'attività HelloWorld in un file denominato HelloWorld.targets e quindi richiamarla da un progetto come indicato di seguito.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Parametri di input e output  
 I parametri dell'attività inline sono elementi figlio di un elemento `ParameterGroup`. Ogni parametro accetta il nome dell'elemento che lo definisce. Il codice seguente definisce il parametro `Text`.  
  
```xml  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 I parametri possono avere uno o più degli attributi seguenti:  
  
-   `Required` è un attributo facoltativo che è `false` per impostazione predefinita. Se `true`, il parametro è obbligatorio e deve avere un valore assegnato prima di chiamare l'attività.  
  
-   `ParameterType` è un attributo facoltativo che è `System.String` per impostazione predefinita. Può essere impostato su qualsiasi tipo completo che sia un elemento o un valore che può essere convertito in e da una stringa usando System.Convert.ChangeType. In altre parole, qualsiasi tipo che può essere passato a e da un'attività esterna.  
  
-   `Output` è un attributo facoltativo che è `false` per impostazione predefinita. Se `true`, il parametro deve avere un valore assegnato prima della restituzione da parte del metodo Execute.  
  
 Ad esempio,  
  
```xml  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 definisce questi tre parametri:  
  
-   `Expression` è un parametro di input obbligatorio del tipo System.String.  
  
-   `Files` è un parametro di input obbligatorio dell'elenco di elementi.  
  
-   `Tally` è un parametro di output del tipo System.Int32.  
  
 Se l'elemento `Code` ha come attributo `Type` `Fragment` o `Method`, le proprietà vengono create automaticamente per ogni parametro. In caso contrario, le proprietà devono essere dichiarate in modo esplicito nel codice sorgente dell'attività e devono corrispondere esattamente alle relative definizioni di parametro.  
  
## <a name="example"></a>Esempio  
 L'attività inline seguente sostituisce ogni occorrenza di un token nel file specificato con il valore specificato.  
  
```xml  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Procedura dettagliata: creazione di un'attività inline](../msbuild/walkthrough-creating-an-inline-task.md)
