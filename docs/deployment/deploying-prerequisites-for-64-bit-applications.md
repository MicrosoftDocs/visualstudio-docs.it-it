---
title: Distribuzione dei prerequisiti per le applicazioni a 64 bit | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6e0134b0a0a6151b6ae6544f1ad8272a6d4cac47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Prerequisiti per la distribuzione di applicazioni a 64 bit
La distribuzione ClickOnce supporta l'installazione di applicazioni su piattaforme a 64 bit. Le piattaforme di destinazione sono **x86** per piattaforme a 32 bit, **x64** per computer che supportano il set di istruzioni AMD64 ed EM64T e **Itanium** per il processore Itanium a 64 bit.  
  
## <a name="prerequisites"></a>Prerequisiti  
 La tabella seguente elenca i componenti ridistribuibili che è possibile usare come prerequisiti per l'installazione dell'applicazione a 64 bit.  
  
 Se si seleziona un prerequisito che non ha componenti a 64 bit, è possibile che venga visualizzato un avviso che indica che i pacchetti selezionati non sono disponibili per la piattaforma a 64 bit.  
  
|Componente ridistribuibile|Supporto x64|Supporto IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Sì|No|  
|Librerie di runtime di Visual C++ 2010 (IA64)|No|Sì|  
|Librerie di runtime di Visual C++ 2010 (x64)|Sì|No|  
|Microsoft .NET Framework 4 (x86 e x64)|Sì||  
|Microsoft .NET Framework 4 Client Profile (x86 e x64)|Yes||  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Applicazioni a 64 bit](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)