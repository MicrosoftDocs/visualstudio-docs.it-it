---
title: Servizi forniti (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6951881e915b44c0cb0c85685280f2b770647f3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="services-provided-source-control-vspackage"></a>Servizi forniti (origine controllo VSPackage)
I servizi sono il meccanismo principale attraverso cui funzionalità è condivisa tra pacchetti VSPackage e tra l'ambiente di sviluppo integrato (IDE) di Visual Studio e il VSPackage installato. Per una descrizione dettagliata dei servizi e la loro importanza nell'IDE di Visual Studio, vedere[sull'utilizzo e la fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Il servizio di controllo di origine  
 Visual Studio fornisce due livelli di servizi, i servizi a livello di IDE e a livello di pacchetto. IDE di Visual Studio in modo nativo fornisce servizi a livello di IDE. Il pacchetto di controllo di origine utilizza alcuni di questi servizi. Il pacchetto di controllo di origine a un VSPackage condivide il controllo del codice sorgente, fornendo un servizio di controllo origine privata del proprio. Il package del controllo del codice sorgente incapsula il set di interfacce correlate al controllo origine implementati dall'oggetto sotto forma di un contratto che può essere usato dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)