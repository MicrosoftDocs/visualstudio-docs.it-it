---
title: Strumenti del servizio immagini | Microsoft Docs
description: Informazioni sugli strumenti disponibili in Visual Studio SDK che consentono di compilare le estensioni usando il servizio immagini di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ddb0342-eb22-429a-bdf3-ccc2719a7ceb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f303fc14b8f463af5d5b5fa2f867ea412e68edae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840067"
---
# <a name="image-service-tools"></a>Strumenti per il servizio immagini
Visual Studio SDK include diversi strumenti che consentono ai generatori di estensioni di usare il servizio immagini di Visual Studio.

- Lo strumento [manifest from resources](../../extensibility/internals/manifest-from-resources.md) accetta un elenco di risorse immagine (file con estensione png o XAML) e genera un file manifesto di immagine.

- Lo strumento [manifest to Code](../../extensibility/internals/manifest-to-code.md) accetta un file manifesto di immagine e genera un file wrapper da usare nei file C++, C#, VB o vsct.

- Il [Visualizzatore della libreria di immagini](../../extensibility/internals/image-library-viewer.md) può caricare, modificare e cercare manifesti di immagini.
