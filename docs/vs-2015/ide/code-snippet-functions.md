---
title: Funzioni dei frammenti di codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a7a7522d0c3ddab224e19150f47120b92b2dd32
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701531"
---
# <a name="code-snippet-functions"></a>Funzioni dei frammenti di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con i frammenti di codice [!INCLUDE[csprcs](../includes/csprcs-md.md)] è possibile usare tre funzioni. Le funzioni sono specificate nell'elemento [Function](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) del frammento di codice. Per informazioni sulla creazione di frammenti di codice, vedere [Frammenti di codice](../ide/code-snippets.md).  
  
## <a name="functions"></a>Funzioni  
 Nella tabella seguente vengono descritte le funzioni disponibili per l'uso con l'elemento `Function` nei frammenti di codice.  
  
|Funzione|Description|Linguaggio|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Genera un'istruzione switch e un set di istruzioni case per i membri dell'enumerazione specificata dal parametro `EnumerationLiteral`. Il parametro `EnumerationLiteral` deve essere un riferimento a un valore letterale di enumerazione o un tipo di enumerazione.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`ClassName()`|Restituisce il nome della classe che contiene il frammento inserito.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Riduce il parametro *TypeName* alla forma più semplice nel contesto in cui il frammento è stato richiamato.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare la funzione `GenerateSwitchCases`. Quando questo frammento viene inserito e un'enumerazione viene immessa nel valore letterale `$switch_on$`, il valore letterale `$cases$` genera un'istruzione `case` per ogni valore presente nell'enumerazione.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare la funzione `ClassName`. Quando questo frammento viene inserito, il valore letterale `$classname$` viene sostituito con il nome della classe contenitore nella posizione corrispondente nel file di codice.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come usare la funzione `SimpleTypeName`. Quando questo frammento viene inserito in un file di codice, il valore letterale `$SystemConsole$` verrà sostituito con la forma più semplice del tipo <xref:System.Console> nel contesto in cui il frammento è stato richiamato.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Function (frammenti di codice IntelliSense)](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
