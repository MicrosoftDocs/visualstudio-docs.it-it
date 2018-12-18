---
title: Numeri di versione dell'assembly principale e degli assembly satellite localizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 361a2ff0d35c71250acca59788c199fbe69f57ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Numeri di versione dell'assembly principale e degli assembly satellite localizzati
La classe <xref:System.Resources.SatelliteContractVersionAttribute> offre il supporto al controllo delle versioni per un assembly principale che usa risorse localizzate tramite la gestione risorse. L'applicazione di <xref:System.Resources.SatelliteContractVersionAttribute> all'assembly principale di un'applicazione consente di aggiornare e ridistribuire l'assembly senza aggiornare i relativi assembly satellite. Ad esempio, è possibile usare la classe <xref:System.Resources.SatelliteContractVersionAttribute> con un Service Pack che non introduce nuove risorse senza ricompilare e ridistribuire gli assembly satellite. Affinché le risorse localizzate siano disponibili, la versione del contratto satellite dell'assembly principale deve corrispondere alla classe <xref:System.Reflection.AssemblyVersionAttribute> degli assembly satellite. È necessario specificare un numero di versione esatto in <xref:System.Resources.SatelliteContractVersionAttribute>; non sono consentiti caratteri jolly come "*". Per altre informazioni, vedere [Recupero di risorse](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).  
  
## <a name="updating-assemblies"></a>Aggiornamento degli assembly  
 La classe <xref:System.Resources.SatelliteContractVersionAttribute> consente di aggiornare un assembly principale senza dover aggiornare l'assembly satellite o viceversa. Quando viene aggiornato l'assembly principale, il numero di versione dell'assembly viene modificato. Se si vuole continuare a usare gli assembly satellite esistenti, modificare il numero di versione dell'assembly principale ma lasciare inalterato il numero di versione del contratto satellite. Ad esempio, nel primo rilascio la versione dell'assembly principale potrebbe essere 1.0.0.0. La versione del contratto satellite e la versione dell'assembly per l'assembly satellite saranno ugualmente 1.0.0.0. Se è necessario aggiornare l'assembly principale di un Service Pack, è possibile modificare la versione dell'assembly su 1.0.0.1, mantenendo la versione del contratto satellite e la versione dell'assembly del satellite come 1.0.0.0.  
  
 Se si vuole aggiornare un assembly satellite ma non l'assembly principale, modificare la classe <xref:System.Reflection.AssemblyVersionAttribute> dell'assembly satellite. Insieme all'assembly satellite, sarà necessario inviare un assembly di criteri che informa che il nuovo assembly satellite è compatibile con l'assembly satellite precedente. Per altre informazioni sui criteri, vedere [Come il runtime individua gli assembly](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
 Il codice seguente indica come impostare la versione del contratto satellite. Il codice può essere inserito in uno script di compilazione o nel file AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come il runtime individua gli assembly](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [Impostazione degli attributi dell'assembly](/dotnet/framework/app-domains/set-assembly-attributes)   
 [Sicurezza e assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)