---
title: Debug di un controllo ActiveX Data-Bound | Microsoft Docs
description: Informazioni su come eseguire il debug di un controllo ActiveX associato a un controllo origine dati mediante la creazione di un'applicazione contenitore per il debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24de30887185ce4520817904ec6348ef6276b6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872898"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debug di un controllo ActiveX con associazione a dati
Quando si sviluppa un controllo ActiveX che verrà associato a un controllo origine dati, è possibile creare un'applicazione contenitore e utilizzare il contenitore per eseguire il debug del controllo ActiveX.

 È ad esempio possibile creare un'applicazione a finestre MFC e inserire nella finestra di dialogo il controllo con associazione a dati e un controllo origine dati. Questa applicazione MFC può essere utilizzata per effettuare test in fase di esecuzione, nonché come eseguibile del contenitore per il debug del controllo ActiveX con associazione a dati.

## <a name="using-the-test-container"></a>Utilizzo di Test Container
 Se si desidera un contenitore facilmente modificabile per il supporto di diverse interfacce sul controllo o sul contenitore, utilizzare ActiveX Test Container come eseguibile per la sessione di debug. In ActiveX Test Container scegliere **Opzioni** dal menu **Contenitore** per attivare le diverse interfacce. Per altre informazioni, vedere [test di proprietà ed eventi con test container](/cpp/mfc/testing-properties-and-events-with-test-container).

 Per eseguire istruzione per istruzione il codice del contenitore durante il debug, utilizzare la versione di debug del contenitore oppure la versione di debug di ActiveX Control Test Container. Per altre informazioni, vedere [esempio TSTCON: ActiveX Control Test Container](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Vedi anche
- [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)
- [Controlli ActiveX](/cpp/mfc/activex-controls)