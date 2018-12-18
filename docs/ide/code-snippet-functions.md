---
title: Funzioni dei frammenti di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cf35e77b5383f2da9dd8c735f216735f405d38ec
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="code-snippet-functions"></a>Funzioni dei frammenti di codice

Con i frammenti di codice C# è possibile usare tre funzioni. Le funzioni sono specificate nell'elemento [Function](../ide/code-snippets-schema-reference.md#function) del frammento di codice. Per informazioni sulla creazione di frammenti di codice, vedere [Frammenti di codice](../ide/code-snippets.md).

## <a name="functions"></a>Funzioni

Nella tabella seguente vengono descritte le funzioni disponibili per l'uso con l'elemento `Function` nei frammenti di codice.

|Funzione|Descrizione|Linguaggio|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Genera un'istruzione switch e un set di istruzioni case per i membri dell'enumerazione specificata dal parametro `EnumerationLiteral`. Il parametro `EnumerationLiteral` deve essere un riferimento a un valore letterale di enumerazione o un tipo di enumerazione.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Restituisce il nome della classe che contiene il frammento inserito.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Riduce il parametro *TypeName* alla forma più semplice nel contesto in cui il frammento è stato richiamato.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## <a name="example"></a>Esempio

L'esempio seguente illustra come usare la funzione `GenerateSwitchCases`. Quando questo frammento viene inserito e un'enumerazione viene immessa nel valore letterale `$switch_on$`, il valore letterale `$cases$` genera un'istruzione `case` per ogni valore presente nell'enumerazione.  

```xml
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

```xml
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
            <Code Language="csharp" Format="CData">  
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

```xml
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

[Elemento Function](../ide/code-snippets-schema-reference.md#function)  
[Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
