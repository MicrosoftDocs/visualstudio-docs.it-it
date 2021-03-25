---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
description: Un file con estensione pkgdef contiene informazioni che altrimenti verrebbero aggiunte al registro di sistema. Informazioni su come Visual Studio USA i file pkgdef per descrivere/individuare un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e2ed8d7c376f7d9f23e06786fefc1a955ebea3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069465"
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa sui file. pkgdef per descrivere e individuare un pacchetto VSPackage. Un file. pkgdef contiene tutte le informazioni di registrazione che altrimenti verrebbero aggiunte al registro di sistema. I pacchetti VSPackage gestiti vengono registrati aggiungendo attributi al codice sorgente e quindi eseguendo l' [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) nell'assembly risultante per generare un file con estensione pkgdef.

## <a name="in-this-section"></a>Contenuto della sezione
- [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Descrive il percorso di caricamento per i pacchetti VSPackage.

- [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Viene illustrato come registrare un pacchetto VSPackage.
