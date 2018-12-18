---
title: "Cenni preliminari sulle proprietà personalizzate dei documenti | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 672eaf3ed82a80983b919a37b2aeff4c99621f43
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview

Quando si compila un progetto a livello di documento, Visual Studio aggiunge due proprietà personalizzate al documento nel progetto: \_PercorsoAssembly e \_AssemblyName. Quando un utente apre un documento, l'applicazione di Microsoft Office controlla per queste proprietà personalizzate dei documenti. Se sono presenti nel documento, l'applicazione carica il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], che avvia la personalizzazione. Per ulteriori informazioni, vedere [architettura di soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Questa proprietà contiene il CLSID di un'interfaccia, il caricatore di soluzioni Office del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Il valore CLSID è 4-491E-A7D4-64AF99AF6E8B 4E3C66D5 - 58D. Non è necessario modificare questo valore.

## <a name="assemblylocation"></a>\_PercorsoAssembly

Questa proprietà contiene una stringa che fornisce informazioni dettagliate su manifesto di distribuzione per la personalizzazione. Per ulteriori informazioni sui manifesti, vedere [Application and Deployment Manifests nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Valore della proprietà The_AssemblyLocation può avere formati diversi, a seconda della modalità di distribuzione della soluzione:

- Se la soluzione viene pubblicata per essere installata da un sito Web, percorso UNC o una CD o un'unità USB, la proprietà AssemblyLocation ha il formato *PercorsoManifestoDistribuzione*|*IDSoluzione*. La stringa seguente è riportato un esempio:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se l'esecuzione o il debug della soluzione da Visual Studio, la proprietà AssemblyLocation ha il formato *NomeDistribuzioneManifesto*|*IDSoluzione*| vstolocal. La stringa seguente è riportato un esempio:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 Il *IDSoluzione* è un GUID che il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilizza per identificare la soluzione. Il *IDSoluzione* viene generato automaticamente quando si compila il progetto. Il **vstolocal** indica al [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che l'assembly deve essere caricato dalla stessa cartella del documento.

## <a name="see-also"></a>Vedere anche

[Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
[architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
[manifesti dell'applicazione e distribuzione nelle soluzioni Office ](../vsto/application-and-deployment-manifests-in-office-solutions.md) 
 [Procedura: pubblicare una soluzione Office tramite ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
[procedura: creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)
