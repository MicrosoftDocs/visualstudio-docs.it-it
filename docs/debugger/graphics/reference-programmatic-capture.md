---
title: Riferimento (acquisizione a livello di codice) | Microsoft Docs
description: Usare l'API di acquisizione a livello di codice per esercitare il controllo a livello di codice sulle funzionalità di acquisizione di Diagnostica della grafica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 452360e04170bbf217c2f6ac0598533f3cab2259
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905102"
---
# <a name="reference-programmatic-capture"></a>Riferimento (acquisizione a livello di codice)
Diagnostica della grafica supporta il controllo a livello di programmazione sulle funzionalità di acquisizione, tramite l'API di acquisizione a livello di programmazione. È possibile utilizzare questa API per attivare o disattivare e aggiungere messaggi alla diagnostica grafica HUD (Head-Up Display), inizializzare e creare file di log di grafica e acquisire informazioni grafiche.

## <a name="programmatic-capture-apis"></a>API di acquisizione a livello di programmazione

### <a name="classes"></a>Classi

|Nome|Descrizione|
|----------|-----------------|
|[Classe VsgDbg](vsgdbg-class.md)|Rappresenta l'interfaccia attraverso cui il componente in-app di diagnostica della grafica è controllato a livello di programmazione.|

### <a name="preprocessor-symbols"></a>Simboli del preprocessore

|Nome|Descrizione|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definisce il nome file predefinito del file di log di grafica.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Quando presente, definisce se viene fornita un'istanza predefinita della classe `VsgDbg`.|

## <a name="related-articles"></a>Articoli correlati

| Titolo | Descrizione |
| - | - |
| [Acquisizione di informazioni grafiche](capturing-graphics-information.md) | Viene indicato come acquisire informazioni grafiche dall'app basata su DirectX per poter usare gli strumenti di diagnostica della grafica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per diagnosticare problemi di rendering. |
| [Overview](overview-of-visual-studio-graphics-diagnostics.md) | Viene indicato come la diagnostica grafica consente di eseguire il debug degli errori di rendering nei giochi e nelle app DirectX. |
