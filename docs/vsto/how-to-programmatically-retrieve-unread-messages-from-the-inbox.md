---
title: Ottenere i messaggi non letti dalla posta in arrivo a livello di codice
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9a718d6a8ee4eb633b34e1e12f85d578dc99fa6
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328934"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Procedura: Recuperano i messaggi non letti dalla posta in arrivo
  Questo esempio richiama messaggi di posta elettronica non letta dalla Outlook **posta in arrivo** e visualizza il numero di elementi.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Introduzione a programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Procedura: A livello di codice crea un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Procedura: A livello di codice Invia messaggio di posta elettronica](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Procedura: A livello di programmazione eseguire azioni quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
