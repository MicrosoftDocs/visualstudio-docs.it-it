---
title: 'Procedura: configurare un Computer per sviluppare soluzioni Office | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b595ead26a88215749c3fb3db382b043f4af4f26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procedura: configurare un computer per sviluppare soluzioni Office
  Per configurare un computer di sviluppo in modo tale da poter utilizzare gli strumenti di sviluppo di Microsoft Office in Visual Studio, seguire le istruzioni in questo argomento. Per seguire la procedura, è necessario disporre dei privilegi amministrativi sul computer di sviluppo.  
  
### <a name="to-configure-the-development-computer"></a>Per configurare il computer di sviluppo  
  
1.  Installare una versione di Visual Studio che includa gli strumenti di sviluppo di Office. Gli strumenti di sviluppo di Office vengono installati per impostazione predefinita. Se si personalizza l'installazione di Visual Studio selezionando le funzionalità da installare, verificare che **Microsoft Office Developer Tools** viene selezionata durante l'installazione. Per ulteriori informazioni sulle versioni di Visual Studio che includono gli strumenti di sviluppo di Office, vedere [configurazione di un Computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installare una versione di Office supportata dagli strumenti di sviluppo di Office in Visual Studio. Per altre informazioni, vedere [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Assicurarsi inoltre di installare gli assembly di interoperabilità primari per la versione di Office installata. Per impostazione predefinita, gli assembly di interoperabilità primari vengono installati con Office. Se si modifica l'installazione di Office, assicurarsi che il **Supporto programmabilità .NET** funzionalità è selezionata per le applicazioni di destinazione.  
  
3.  Se si dispone di una versione in lingua inglese di Visual Studio ma impostazioni non in lingua inglese per Windows, è possibile installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] language pack per visualizzare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] messaggi nella stessa lingua di Windows. Le versioni non in lingua inglese di Visual Studio installano automaticamente il language pack. Il language pack è disponibile il [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vedere anche  
 [Novità nello sviluppo per Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Introduzione al &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Procedura: installare Visual Studio Tools per Office Runtime ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Procedura: Installare l'assembly di interoperabilità primario di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  