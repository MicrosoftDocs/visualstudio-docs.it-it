---
title: 'Estensione Excel di esempio: classe PropertyProvider | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a3da33b0c99c84f3680f323b483cebf31448ba62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Estensione Excel di esempio: classe PropertyProvider
Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornisce servizi di proprietà per gli elementi di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] per la registrazione e la riproduzione dei test dell'interfaccia utente.

## <a name="getcontrolsupportlevel-method"></a>Metodo GetControlSupportLevel
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> restituisce un numero che indica il livello di supporto che il provider di proprietà può offrire per il controllo specificato. Più alto è il valore restituito, maggiore è il livello di supporto del controllo offerto dal provider di proprietà. In questo caso, il metodo controlla il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del controllo specificato. Se il valore è "Excel" e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica che si tratta di un `CellElement`, il metodo restituisce il valore più elevato. In caso contrario, restituisce zero, che indica che non viene fornito alcun supporto.

## <a name="getpropertynames-method"></a>Metodo GetPropertyNames
 Restituisce un dizionario di nomi di proprietà e descrittori di proprietà per le proprietà supportate di un controllo di cella di Excel.

## <a name="getpropertydescriptor-method"></a>Metodo GetPropertyDescriptor
 Questo metodo viene chiamato dal framework di test per ottenere il descrittore di proprietà predefinito per il nome di proprietà specificato.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metodi GetPropertyValue e SetPropertyValue
 Il metodo `GetPropertyValue` usa la classe `Communicator` dell'estensione per restituire il valore della proprietà da Excel. Il metodo `SetPropertyValue` usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> e il componente `Communicator` per impostare il valore della proprietà. Questi metodi vengono chiamati dal framework di test.

## <a name="code-generation-customization-methods"></a>Metodi di personalizzazione della generazione di codice
 Questi metodi non sono implementati per questa estensione. Di conseguenza, restituiscono `null` o generano l'eccezione <xref:System.NotImplementedException>.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
