---
title: Distribuzione dei tipi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2171a940951d828df358d09dae5fec68b6475e4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-project-types"></a>Tipi di progetto di distribuzione
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Installa un nuovo Sil aggregator di tipi di progetto (ProjectAggregator2. dll) e anche un pacchetto Windows Installer per la ridistribuzione (ProjectAggregator2.msi). È necessario utilizzare il nuovo Sil aggregator per tipi di progetto di codice gestito. ProjectAggregator2 funziona alternative limitazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregator che impediscono il corretto funzionamento tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare al nuovo Sil aggregator.  
  
1.  Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2.  Rimuovere tutti i file binari NativeHierarchyWrapper dall'installazione.  
  
3.  Aggiungere ProjectAggregator2.msi alla propria configurazione.