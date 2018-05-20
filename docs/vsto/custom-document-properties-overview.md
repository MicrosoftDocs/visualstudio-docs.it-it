---
title: Cenni preliminari sulle proprietà personalizzate dei documenti
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>Cenni preliminari sulle proprietà personalizzate dei documenti

Quando si compila un progetto a livello di documento, Visual Studio aggiunge due proprietà personalizzate al documento nel progetto: \_PercorsoAssembly e \_AssemblyName. Quando un utente apre un documento, l'applicazione di Microsoft Office controlla per queste proprietà personalizzate dei documenti. Se sono presenti nel documento, l'applicazione carica il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], che avvia la personalizzazione. Per altre informazioni, vedere [soluzioni di architettura di Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Questa proprietà contiene il CLSID di un'interfaccia, il caricatore di soluzioni Office del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Il valore CLSID è 4-491E-A7D4-64AF99AF6E8B 4E3C66D5 - 58D. Non è necessario modificare questo valore.

## <a name="assemblylocation"></a>\_PercorsoAssembly

Questa proprietà contiene una stringa che fornisce informazioni dettagliate su manifesto di distribuzione per la personalizzazione. Per ulteriori informazioni sui manifesti, vedere [manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Valore della proprietà The_AssemblyLocation può avere formati diversi, a seconda della modalità di distribuzione della soluzione:

- Se la soluzione viene pubblicata per essere installata da un sito Web, percorso UNC o una CD o un'unità USB, la proprietà AssemblyLocation ha il formato *PercorsoManifestoDistribuzione*|*IDSoluzione*. La stringa seguente è riportato un esempio:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se l'esecuzione o il debug della soluzione da Visual Studio, la proprietà AssemblyLocation ha il formato *NomeDistribuzioneManifesto*|*IDSoluzione*| vstolocal. La stringa seguente è riportato un esempio:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 Il *IDSoluzione* è un GUID che il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilizza per identificare la soluzione. Il *IDSoluzione* viene generato automaticamente quando si compila il progetto. Il **vstolocal** indica al [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che l'assembly deve essere caricato dalla stessa cartella del documento.

## <a name="see-also"></a>Vedere anche

- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Procedura: pubblicare una soluzione Office tramite ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Procedura: creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)
