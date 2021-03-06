---
title: Caratteri speciali di MSBuild | Microsoft Docs
description: Informazioni sui caratteri riservati di MSBuild per l'uso speciale in contesti specifici e quando e come eseguire l'escape di questi caratteri.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c5db0b870e050a9235f719d83710747101b95c3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922525"
---
# <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild

MSBuild riserva alcuni caratteri per usi speciali in contesti specifici. L'escape di tali caratteri è necessario solo se devono essere usati letteralmente nel contesto in cui sono riservati. Ad esempio, un asterisco ha un significato speciale solo negli attributi `Include` e `Exclude` di una definizione di elemento e nelle chiamate a `CreateItem`. Se un asterisco deve apparire come asterisco in uno di questi contesti, è necessario eseguirne l'escape. In ogni altro contesto, è sufficiente digitare l'asterisco nel punto in cui deve essere visualizzato.

 Per eseguire l'escape di un carattere speciale, usare la sintassi% \<xx> , dove \<xx> rappresenta il valore esadecimale ASCII del carattere. Per altre informazioni, vedere [procedura: eseguire l'escape dei caratteri speciali in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Caratteri speciali

 Nella tabella seguente sono elencati i caratteri speciali di MSBuild:

|**Carattere**|**ASCII**|**Utilizzo riservato**|
|-------------------|---------------|------------------------|
|%|%25|Riferimento ai metadati|
|$|%24|Riferimento alle proprietà|
|@|%40|Riferimento a elenchi di elementi|
|'|%27|Condizioni e altre espressioni|
|;|%3B|Separatore di elenco|
|?|%3F|Carattere jolly per i nomi di file negli attributi `Include` e `Exclude`|
|*|%2A|Carattere jolly per l'uso nei nomi di file negli attributi `Include` e `Exclude`|

## <a name="see-also"></a>Vedi anche

- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
- [Elementi](../msbuild/msbuild-items.md)
