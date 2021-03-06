---
title: Elemento Include | Microsoft Docs
description: L'elemento Include specifica un file che può essere posizionato nel percorso di inclusione fornito per l'inserimento nel file corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0005626c7fbb276775661a7cfb73d17f5e20d62
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899355"
---
# <a name="include-element"></a>Elemento Include
L'elemento Include specifica un file che può essere posizionato nel percorso di inclusione fornito per l'inserimento nel file corrente.  Tutti i simboli e i tipi definiti diventeranno parte del risultato compilato.

## <a name="syntax"></a>Sintassi

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href="stdidcmd.h"|
|Condizione|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano comandi, ovvero voci di menu, menu, barre degli strumenti e caselle combinate, forniti da un vspackage all'IDE.|

## <a name="example"></a>Esempio

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Vedere anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
