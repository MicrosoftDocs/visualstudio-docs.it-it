---
title: Sicurezza e assembly satellite localizzati | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5f2834e267e2494f62f5cfed9121a0a94a22afb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicurezza e assembly satellite localizzati

Se l'assembly principale usa la funzione di nome sicuro, gli assembly satellite devono essere firmati con la stessa chiave privata dell'assembly principale. Se la coppia chiave pubblica/chiave privata degli assembly satellite e dell'assembly principale non corrisponde, le risorse non verranno caricate. Per altre informazioni sulla firma degli assembly, vedere [Procedura: Firmare un assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 In genere, può essere necessario che il gruppo di firma dell'organizzazione o un società di firma esterna usino per la firma la chiave privata. Tale necessità è dovuta alla natura della chiave privata: l'accesso è spesso limitato solo a pochi individui. Durante lo sviluppo è possibile usare la firma posticipata. Per ulteriori informazioni, vedere [Ritardo della firma di un assembly](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>Vedere anche

- [Considerazioni sulla sicurezza degli assembly](/dotnet/framework/app-domains/assembly-security-considerations)  - [Concetti principali sulla sicurezza](/dotnet/standard/security/key-security-concepts)   
- [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
- [Localizzazione di applicazioni](../ide/localizing-applications.md)   
- [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)