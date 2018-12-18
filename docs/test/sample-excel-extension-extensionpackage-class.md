---
title: 'Estensione Excel di esempio: classe ExtensionPackage | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 623b18a22441fdd2478716582d94a8b878c31d54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Estensione Excel di esempio: classe ExtensionPackage
Questa classe estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e offre il punto di ingresso per un test codificato dell'interfaccia utente per un foglio di lavoro di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

## <a name="assembly-attribute"></a>Attributo Assembly
 Il file inizia con un attributo Assembly che identifica l'assembly come un'estensione di test dell'interfaccia utente.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Questo attributo dichiara il nome della classe di base, il nome della classe del pacchetto e il nome completo della classe per la classe del pacchetto di estensione personalizzato.

## <a name="simple-properties"></a>Proprietà semplici
 Questa classe dispone di proprietà che forniscono i valori usati dal framework dei test codificati dell'interfaccia utente per identificare e descrivere l'estensione e l'assembly. Per altre informazioni, vedere i commenti del codice.

## <a name="getservice-method"></a>Metodo GetService
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> è il singolo punto di ingresso usato dal framework dei test codificati dell'interfaccia utente per accedere al gestore della tecnologia, al provider di proprietà e al filtro delle azioni, come identificato dalla classe di base per ogni oggetto.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
