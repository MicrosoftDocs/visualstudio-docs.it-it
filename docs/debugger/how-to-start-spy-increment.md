---
title: Avvia Spy + + | Microsoft Docs
description: Informazioni su come avviare lo strumento Spy + + da Visual Studio o dal prompt dei comandi quando si desidera eseguire il debug di una soluzione.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896628"
---
# <a name="how-to-start-spy"></a>Procedura: avviare Spy++

È possibile avviare Spy + + da Visual Studio o dal prompt dei comandi.

 Quando si avvia Spy + +, se viene visualizzato un messaggio per richiedere l'autorizzazione per apportare modifiche al computer, selezionare **Sì**.

> [!NOTE]
> È possibile eseguire una sola istanza di Spy + +. Se si tenta di avviare una seconda istanza, solo l'istanza attualmente in esecuzione ottiene lo stato attivo.

## <a name="prerequisites"></a>Prerequisiti

Spy + + richiede i componenti seguenti. È possibile selezionare questi componenti dal Programma di installazione di Visual Studio selezionando la scheda **singoli componenti** e quindi selezionando i componenti seguenti.

* In debug e test selezionare strumenti per la **profilatura C++**
* In attività di sviluppo selezionare **funzionalità di base di C++**

Se sono state apportate modifiche, seguire le istruzioni per installare questi componenti.

## <a name="start-spy-from-visual-studio"></a>Avviare Spy + + da Visual Studio

Scegliere **Spy + +** dal menu **strumenti** .

Poiché Spy + + viene eseguito in modo indipendente, dopo averla avviata è possibile chiudere Visual Studio.

> [!NOTE]
> Quando si registrano messaggi con Spy + +, può causare un rallentamento del sistema operativo.

## <a name="start-spy-at-a-command-prompt"></a>Avviare Spy + + al prompt dei comandi

1. In una finestra del prompt dei comandi passare alla cartella che contiene spyxx.exe. In genere, il percorso di questa cartella è.. \\ *Cartella di installazione di Visual Studio*\Common7\Tools \\ .

2. Immettere **spyxx.exe**.

## <a name="see-also"></a>Vedi anche
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)
