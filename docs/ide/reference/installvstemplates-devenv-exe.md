---
title: Opzione /InstallVSTemplates (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

L'opzione /InstallVSTemplates consente di registrare modelli di progetto o di elemento che si trovano in *\<percorso di installazione di Visual Studio>*\Common7\IDE\ProjectTemplates\ o *\<percorso di installazione di Visual Studio>*\Common7\IDE\ItemTemplates\ per potervi accedere dalle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**.

> [!WARNING]
> Questa opzione è supportata solo per lo sviluppo partner di Visual Studio. Per poter usare le opzioni [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) è necessario eseguire devenv come amministratore. Per altre informazioni, vedere [User Permissions](../../ide/user-permissions-and-visual-studio.md) (Autorizzazioni utente).

## <a name="syntax"></a>Sintassi

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Vedere anche

[Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)