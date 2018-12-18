---
title: 'Procedura: Specificare il file binario da avviare | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac87c771cf6d9515f3eae8d82f7d0d40fa6590a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-binary-to-start"></a>Procedura: Specificare l'inizio del file binario

Per profilare file binari, ad esempio le DLL, è necessario immettere informazioni nella finestra di dialogo **Pagine delle proprietà di \<destinazione>**. Queste informazioni indicano dove il progetto DLL può trovare l'applicazione chiamante.

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul file binario di destinazione e quindi scegliere **Proprietà**.

2. Nella finestra di dialogo **Pagine delle proprietà** fare clic sulle proprietà di **Avvio**.

3. Selezionare la casella di controllo **Eseguire l'override delle impostazioni progetto**.

4. Nella casella di testo **Eseguibile da avviare** specificare il percorso del file.

5. Nella casella di testo **Argomenti** specificare gli argomenti necessari per avviare l'applicazione.

6. Nella casella di testo **Directory di lavoro** specificare il percorso della directory.

7. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

[Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)