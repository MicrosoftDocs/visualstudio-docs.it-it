---
title: '&lt;&gt;elemento Description (sviluppo per Office in Visual Studio)'
description: Informazioni che l'elemento Description dello spazio dei nomi vstov4 archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo componenti aggiuntivi COM.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f065dd07e901ee0d59b39f1096cc351cd70bc02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897596"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento Description (sviluppo per Office in Visual Studio)
  L'elemento `description` dello spazio dei nomi `vstov4` archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.

## <a name="syntax"></a>Sintassi

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 facoltativo. L'elemento `description` si trova nello spazio dei nomi `vstov4` . Contiene la descrizione del componente aggiuntivo che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.

 L'elemento `description` è privo di attributi o elementi.

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `description` in una soluzione a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)