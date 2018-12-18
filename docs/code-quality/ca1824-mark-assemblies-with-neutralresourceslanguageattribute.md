---
title: 'CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Category|Microsoft. Performance|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un assembly contiene un **ResX**-risorsa basata su ma non dispone di <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> applicato.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il **NeutralResourcesLanguage** attributo indica il **ResourceManager** del linguaggio utilizzato per visualizzare le risorse della lingua per un assembly. Durante la ricerca di risorse con le stesse impostazioni cultura per la lingua risorse neutra, le **ResourceManager** utilizza automaticamente le risorse che si trovano nell'assembly principale. Ciò avviene invece di cercare un assembly satellite con le impostazioni cultura dell'interfaccia utente corrente per il thread corrente. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.  
  
## <a name="fixing-violations"></a>Correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly, specificare la lingua delle risorse della lingua.  
  
## <a name="specifying-the-language"></a>Specifica della lingua  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Per specificare la lingua della risorsa delle impostazioni cultura neutre  
  
1.  In **Esplora**mouse sul progetto e quindi fare clic su **proprietà**.  
  
2.  Dalla barra di spostamento a sinistra selezionare **applicazione**, quindi fare clic su **informazioni sull'Assembly**.  
  
3.  Nel **informazioni sull'Assembly** finestra di dialogo, selezionare la lingua dal **indipendente dalla lingua** elenco a discesa.  
  
4.  Fare clic su **OK**.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consentito escludere un avviso da questa regola. Tuttavia, è potrebbero ridurre le prestazioni di avvio.