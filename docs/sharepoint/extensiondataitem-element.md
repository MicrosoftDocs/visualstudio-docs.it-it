---
title: Elemento ExtensionDataItem | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento ExtensionDataItem, che è un elemento nello schema dell'elemento del progetto SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: add1a119283635f9cfd9bebddfe18228f1976703
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876823"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem (elemento)
  Elemento di dati personalizzato associato all'elemento del progetto SharePoint, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.

## <a name="syntax"></a>Sintassi

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Chiave**|Attributo **xs: String** obbligatorio.<br /><br /> Chiave utilizzata per archiviare e recuperare l'elemento dati.|
|**Valore**|Attributo **xs: String** obbligatorio.<br /><br /> Valore dell'elemento di dati.|

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento del progetto SharePoint.|

## <a name="remarks"></a>Commenti
 Quando si associano dati personalizzati a un elemento del progetto SharePoint usando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto, Visual Studio salva i dati in un nuovo elemento **ExtensionDataItem** nel `.spdata` file per l'elemento di progetto. Per ulteriori informazioni, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
