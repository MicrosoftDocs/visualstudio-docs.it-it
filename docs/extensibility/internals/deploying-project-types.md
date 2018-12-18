---
title: Distribuzione dei tipi di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>Tipi di progetto di distribuzione
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Installa un nuovo Sil aggregator di tipi di progetto (ProjectAggregator2. dll) e anche un pacchetto Windows Installer per la ridistribuzione (ProjectAggregator2.msi). È necessario utilizzare il nuovo Sil aggregator per tipi di progetto di codice gestito. ProjectAggregator2 funziona alternative limitazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregator che impediscono il corretto funzionamento tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare al nuovo Sil aggregator.  
  
1.  Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2.  Rimuovere tutti i file binari NativeHierarchyWrapper dall'installazione.  
  
3.  Aggiungere ProjectAggregator2.msi alla propria configurazione.