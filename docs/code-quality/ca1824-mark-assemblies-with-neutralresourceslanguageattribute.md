---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8714df15bb7905aa1a7f895a8d5c197ff3796383
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un assembly contiene un **ResX**-risorsa basata su ma non dispone di <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> applicato.

## <a name="rule-description"></a>Descrizione della regola

Il <xref:System.Resources.NeutralResourcesLanguageAttribute> attributo informa il gestore delle risorse di impostazioni cultura predefinite dell'app. Se le risorse di impostazioni cultura predefinite vengono incorporate nell'assembly principale dell'app, e <xref:System.Resources.ResourceManager> deve recuperare le risorse che appartengono alle stesse impostazioni cultura come le impostazioni cultura predefinite, il <xref:System.Resources.ResourceManager> utilizza automaticamente le risorse che si trovano nell'assembly principale invece di cercare un assembly satellite. Questa operazione consente di ignorare il probe assembly normale, migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.

> [!TIP]
> Vedere [creazione di pacchetti e distribuzione delle risorse](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) per il processo che <xref:System.Resources.ResourceManager> viene utilizzato per verificare la presenza di file di risorse.

## <a name="fix-violations"></a>Correggere le violazioni

Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly, specificare la lingua delle risorse della lingua.

### <a name="to-specify-the-neutral-language-for-resources"></a>Per specificare la lingua neutra per le risorse

1. In **Esplora soluzioni**destro del mouse sul progetto e quindi selezionare **proprietà**.

2. Selezionare il **applicazione** scheda e quindi selezionare **informazioni sull'Assembly**.

   > [!NOTE]
   > Se il progetto è un progetto .NET Standard o .NET Core, selezionare il **pacchetto** scheda.

3. Selezionare la lingua dal **lingua neutra** oppure **lingua neutra Assembly** elenco a discesa.

4. Scegliere **OK**.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

È consentito escludere un avviso da questa regola. Tuttavia, potrebbero influire negativamente sulle prestazioni di avvio.

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Risorse nelle applicazioni desktop (.NET)](/dotnet/framework/resources/)
- [CA1703: le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - stringa di risorsa parole composte devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)