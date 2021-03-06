---
title: Manifest to Code | Microsoft Docs
description: Informazioni su come usare lo strumento Manifesto dal codice che accetta un file con estensione imagemanifest da usare con il Visual Studio Image Service.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 17ecacea-397d-4a97-b003-01bd5d56e936
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e63349b27ec8ea5617f6d1836ce9ece3251662d3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903165"
---
# <a name="manifest-to-code"></a>Manifest to Code
Lo strumento Manifest to Code è un'applicazione console che accetta un file con estensione imagemanifest per il servizio immagini Visual Studio e genera uno o più file wrapper per fare riferimento ai valori del manifesto dell'immagine nei file C++, C#, VB o vsct per le estensioni Visual Studio. Questo strumento genera file wrapper che possono essere usati per richiedere immagini direttamente dal servizio immagini di Visual Studio o per passare i valori del manifesto tramite le API se il codice non gestisce la propria interfaccia utente e il rendering.

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Sintassi**

 ManifestToCode /manifest: \<Image Manifest file> /language: \<Code Language>\<Optional Args>

 **Argomenti**

|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|
|-|-|-|
|/manifest|Percorso del manifesto dell'immagine da usare per creare o aggiornare il wrapper del codice.|Obbligatoria|
|/language|Linguaggio in cui generare il wrapper di codice.<br /><br /> Valori validi: CPP, C++, CS, CSharp, C#, VB o VSCT I valori non distinzione tra maiuscole e minuscole.<br /><br /> Per l'opzione del linguaggio VSCT, le opzioni /monikerClass, /classAccess e /namespace vengono ignorate.|Obbligatoria|
|/imageIdClass|Nome di imageIdClass e del file associato creato dallo strumento. Per l'opzione del linguaggio C++, vengono generati solo i file con estensione h.<br /><br /> Impostazione predefinita: \<Manifest Path> \MyImageIds.\<Lang Ext>|Facoltativo|
|/monikerClass|Nome della classe monikerClass e del file associato creato dallo strumento. Per l'opzione del linguaggio C++, vengono generati solo i file con estensione h. Questo valore viene ignorato per il linguaggio VSCT.<br /><br /> Impostazione predefinita: \<Manifest Path> \MyMonikers.\<Lang Ext>|Facoltativo|
|/classAccess|Modificatore di accesso per imageIdClass e monikerClass. Verificare che il modificatore di accesso sia valido per il linguaggio specificato. Questa opzione viene ignorata per l'opzione del linguaggio VSCT.<br /><br /> Impostazione predefinita: Pubblico|Facoltativo|
|/namespace|Spazio dei nomi definito nel wrapper di codice. Questa opzione viene ignorata per l'opzione del linguaggio VSCT. '.' o '::' sono separatori di spazi dei nomi validi, indipendentemente dall'opzione della lingua scelta.<br /><br /> Impostazione predefinita: MyImages|Facoltativo|
|/noLogo|L'impostazione di questo flag impedisce la stampa delle informazioni sul prodotto e sul copyright.|Facoltativo|
|/?|Stampare le informazioni della Guida.|Facoltativo|
|/help|Stampare le informazioni della Guida.|Facoltativo|

 **Esempi**

- ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:CSharp

- ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:C++ /namespace:My::Namespace /imageIdClass:MyImageIds /monikerClass:MyMonikers /classAccess:friend

- ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:VSCT /imageIdClass:MyImageIds

## <a name="notes"></a>Note

- È consigliabile usare questo strumento con manifesti di immagine generati dallo strumento Manifest from Resources.

- Lo strumento esamina solo le voci di simboli per generare i wrapper di codice. Se un manifesto dell'immagine non contiene simboli, i wrapper di codice generati saranno vuoti. Se nel manifesto dell'immagine è presente un'immagine o un set di immagini che non usano simboli, verranno escluse dal wrapper di codice.

## <a name="sample-output"></a>Output di esempio
 **Wrapper C#**

 Una coppia di classi semplici di ID immagine e moniker di immagine per C# sarà simile al codice seguente:

```csharp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using System;

namespace MyImages
{
    public static class MyImageIds
    {
        public static readonly Guid AssetsGuid = new Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}");

        public const int MyImage1 = 0;
        public const int MyImage2 = 1;
    }
}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using Microsoft.VisualStudio.Imaging.Interop;

namespace MyImages
{
    public static class MyMonikers
    {
        public static ImageMoniker MyImage1 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage1 }; } }
        public static ImageMoniker MyImage2 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage2 }; } }
    }
}
```

 **Wrapper C++**

 Una coppia di classi semplici di ID immagine e moniker di immagine per C++ sarà simile al codice seguente:

```cpp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include <guiddef.h>

namespace MyImages {

class MyImageIds {
public:

    static const GUID AssetsGuid;

    static const int MyImage1 = 0;
    static const int MyImage2 = 1;

};

__declspec(selectany) const GUID MyImageIds::AssetsGuid = {0x442d8739,0xefde,0x46a4,{0x8f,0x29,0xe3,0xa1,0xe5,0xe7,0xf8,0xb4}};

}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include "ImageParameters140.h"
#include "MyImageIds.h"

namespace MyImages {

class MyMonikers {
public:

    static const ImageMoniker MyImage1;
    static const ImageMoniker MyImage2;

};

__declspec(selectany) const ImageMoniker MyMonikers::MyImage1 = { MyImageIds::AssetsGuid, MyImageIds::MyImage1 };
__declspec(selectany) const ImageMoniker MyMonikers::MyImage2 = { MyImageIds::AssetsGuid, MyImageIds::MyImage2 };

}
```

 **Visual Basic wrapper**

 Una coppia di classi semplici di ID immagine e moniker di immagine per Visual Basic sarà simile al codice seguente:

```vb
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports System

Namespace MyImages

    Public Module MyImageIds

        Public Shared ReadOnly AssetsGuid As Guid = New Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}")

        Public Const MyImage1 As Integer = 0
        Public Const MyImage2 As Integer = 1

    End Module

End Namespace
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports Microsoft.VisualStudio.Imaging.Interop

Namespace MyImages

    Public Module MyMonikers

        Public Readonly Property MyImage1
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage1}
            End Get
        End Property

        Public Readonly Property MyImage2
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage2}
            End Get
        End Property

    End Module

End Namespace
```

 **Wrapper VSCT**

 Un set di ID immagine per un file con estensione vsct sarà simile al seguente:

```xml
<?xml version='1.0' encoding='utf-8'?>
<!--
- [auto-generated]
     This code was generated by the ManifestToCode tool.
     Tool Version: 14.0.15198
- [/auto-generated]
-->
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
  <Symbols>
    <GuidSymbol name="AssetsGuid" value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}">
      <IDSymbol name="MyImage1" value="0" />
      <IDSymbol name="MyImage2" value="1" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```
