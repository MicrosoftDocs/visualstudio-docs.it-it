---
title: Elemento RequiredFrameworkVersion (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc1a138c50c0fe13962f6601449eb3498d90398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (modelli di Visual Studio)

Specifica la versione minima di .NET Framework richiesta dal modello. Provoca la **versione Framework di destinazione** elenco a discesa per essere visualizzato nel **nuovo progetto** finestra di dialogo. Il `RequiredFrameworkVersion` elemento determina anche il valore più basso disponibile nell'elenco a discesa.

> [!IMPORTANT]
> A partire da Visual Studio 2017 versione 15,6, il **versione Framework di destinazione** elenco a discesa non è più un filtro per i modelli visualizzati nel **modelli** sezione del **nuovo progetto** finestra di dialogo. Al contrario, l'elenco a discesa funziona come un selettore di framework per il modello selezionato.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Sintassi

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come vengono visualizzati in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere il numero di versione minima di .NET Framework che è necessario per il modello.

## <a name="remarks"></a>Note

`RequiredFrameworkVersion` è un elemento facoltativo. Utilizzare questo elemento solo se il modello supporta una versione minima specifica (e versioni successive, se presente) di .NET Framework. Se si specifica il `RequiredFrameworkVersion` elemento e il modello non supporta una specifica versione minima di .NET Framework, il **versione Framework di destinazione** elenco a discesa vengono visualizzati quando non è applicabile.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

In questo esempio, la versione minima di .NET Framework richiesto dal modello, rappresentato da `RequiredFrameworkVersion`, 3.0. Un progetto creato con questo modello può destinate alle versioni di .NET Framework a partire da 3.0.

## <a name="see-also"></a>Vedere anche

- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
