---
title: Debug di COM e ActiveX | Microsoft Docs
description: Suggerimenti per il debug di applicazioni COM e controlli ActiveX in Visual Studio. Informazioni sul debug dei server e dei contenitori COM. Trova gli strumenti di debug COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f86f072a32bf9d7ff4af3c77564236fe2997f70a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865865"
---
# <a name="com-and-activex-debugging"></a>Debug di COM e ActiveX
In questa sezione vengono forniti suggerimenti sul debug di applicazioni COM e di controlli ActiveX.

## <a name="in-this-section"></a>Contenuto della sezione
 [Server com e debug del contenitore](../debugger/com-server-and-container-debugging.md) Menziona considerazioni speciali per il debug di applicazioni COM. I problemi includono: debug di un server e di un contenitore COM tramite due progetti all'interno della stessa soluzione, traccia di chiamate che attraversano i limiti dei processi, impostazione di punti di interruzione in funzioni di callback ed esecuzione delle istruzioni attraverso e all'interno di contenitori e server.

 [Procedura: eseguire il debug di un controllo ActiveX](../debugger/how-to-debug-an-activex-control.md) Contiene informazioni sul debug di controlli ActiveX. quali: specifica di un contenitore relativo alla sessione di debug per visualizzare come viene eseguito il codice nel controllo ActiveX, debug di un controllo ActiveX con associazione a dati, simulazione di un particolare contenitore ed esecuzione passo passo del codice del contenitore.

 [Strumenti di debug com](../debugger/com-debugging-tools.md) Elenca i visualizzatori e le applicazioni di esempio che possono essere utili per eseguire il debug dell'applicazione COM.

## <a name="related-sections"></a>Sezioni correlate
 [Prima di tutto esaminare il debugger](../debugger/debugger-feature-tour.md) Vengono forniti collegamenti alle sezioni più grandi della documentazione di debug. Le informazioni includono: novità del debugger, impostazioni e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti C++, debug di COM e ActiveX, debug di dll, debug di SQL e riferimenti all'interfaccia utente.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Introduzione a COM](/cpp/atl/introduction-to-com)
- [Controlli ActiveX](/cpp/mfc/activex-controls)
- [Applicazioni server SDI](com-server-and-container-debugging.md)