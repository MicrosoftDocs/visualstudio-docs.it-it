---
title: -LCID (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv LCID per impostare la lingua predefinita usata per testo, valuta e altri valori all'interno dell'IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e5aad581babafe882fccc13e8594aa60437d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852141"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Imposta la lingua predefinita usata per testo, valuta e altri valori all'interno dell'IDE.

## <a name="syntax"></a>Sintassi

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argomenti

- *LocaleID*

  Obbligatorio. Identificatore delle impostazioni locali (LCID) della lingua specificata.

## <a name="remarks"></a>Commenti

Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica viene mantenute tra le sessioni e l'IDE Mostra questa modifica nella casella **strumenti**  >  **Opzioni**  >  **ambiente**  >  **impostazioni internazionali**  >   .

Se la lingua specificata non è disponibile nel sistema in uso, l'opzione `/LCID` viene ignorata.

Nella tabella seguente vengono elencati gli LCID delle lingue supportate da Visual Studio.

|Linguaggio|LCID|
|--------------|----------|
|Cinese (semplificato)|2052|
|Cinese (tradizionale)|1028|
|Ceco|1029|
|Inglese|1033|
|Francese|1036|
|Tedesco|1031|
|Italiano|1040|
|Giapponese|1041|
|Coreano|1042|
|Polacco|1045|
|Portoghese (Brasile)|1046|
|Russo|1049|
|Spagnolo|3082|
|Turco|1055

## <a name="example"></a>Esempio

In questo esempio viene caricato l'IDE con le stringhe delle risorse in lingua inglese.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md)
