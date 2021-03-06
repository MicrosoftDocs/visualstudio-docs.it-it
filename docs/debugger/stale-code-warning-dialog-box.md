---
title: Finestra di dialogo avviso di codice non aggiornato | Microsoft Docs
description: Leggere la finestra di dialogo avviso di codice non aggiornato, che viene visualizzato quando sono state apportate modifiche al codice nativo che modifica e continuazione non possono essere applicate immediatamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4ea2004680a60fcd2c90a57b19f719c0412ee53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861244"
---
# <a name="stale-code-warning-dialog-box"></a>Avviso di codice non aggiornato (finestra di dialogo)

Questa finestra di dialogo viene visualizzata quando vengono apportate modifiche al codice nativo che la modalità **Modifica e continuazione** non può applicare immediatamente. Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato. Per altre informazioni, vedere [Modifica e continuazione (C++)](edit-and-continue-visual-cpp.md).

**Non visualizzare più questo messaggio**

Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione. Per riattivare questo messaggio di avviso, accedere alla finestra di dialogo **Opzioni**, aprire la cartella **Debug**, fare clic sulla pagina **Modifica e continuazione** e selezionare **Avvisa in caso di codice non aggiornato**.

## <a name="see-also"></a>Vedi anche

- [Modifiche al codice supportate (C++)](supported-code-changes-cpp.md)
- [Modifica e continuazione, Debug, finestra di dialogo Opzioni](edit-and-continue.md)