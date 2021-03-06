---
title: Abilitazione del debug di un programma | Microsoft Docs
description: Informazioni su come avviare il motore di debug o alleghi il motore di debug a un programma esistente per eseguire il debug di un programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ed7ce97e6ff7e8801953877ed80afa7ca262f20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097227"
---
# <a name="enable-a-program-to-be-debugged"></a>Abilitare un programma di cui eseguire il debug
Prima che il motore di debug (DE) possa eseguire il debug di un programma, è necessario prima avviare il DE o collegarlo a un programma esistente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Ottenere una porta](../../extensibility/debugger/getting-a-port.md) Viene illustrato come ottenere una porta come primo passaggio per consentire il debug di un programma.

 [Registrare il programma](../../extensibility/debugger/registering-the-program.md) Viene illustrato il passaggio successivo per abilitare un programma di cui eseguire il debug: registrazione con la porta. Una volta registrato, il programma può essere sottoposto a debug dal processo di connessione o debug JIT (just-in-Time).

 [Connetti al programma](../../extensibility/debugger/attaching-to-the-program.md) Viene illustrato il passaggio successivo: associazione del debugger al programma.

 [Connessione basata su avvio](../../extensibility/debugger/launch-based-attachment.md) Descrive l'allegato basato sul lancio a un programma, che è automatico all'avvio da parte di SDM.

 [Invia gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md) Vengono illustrati gli eventi necessari durante la creazione di un motore di debug (DE) e la relativa associazione a un programma.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definisce un motore di debug (DE) e descrive i servizi implementati tramite le interfacce DE e il modo in cui possono determinare la transizione del debugger tra diverse modalità operative.
